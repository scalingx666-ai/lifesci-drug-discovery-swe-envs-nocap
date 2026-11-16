# Issue

**Title:** Ersilia improvements

## Description

Thank you for taking your time to contribute to Ersilia, just a few checks before we proceed
- [x] Have you followed the guidelines in our [Contribution Guide](https://github.com/ersilia-os/ersilia/blob/master/CONTRIBUTING.md)
- [x] Have you written new tests for your core changes, as applicable?
- [x] Have you successfully ran tests with your changes locally?

**Description**

This PR fixes four bugs: a stalling fetch when Git LFS is not installed, a Docker socket mismatch on Linux with Docker Desktop, Docker images being deleted by the wrong user on shared machines, and missing DOI validation for peer-reviewed publications.

**Changes to be made**

- **Git LFS error message** (ersilia/hub/fetch/actions/setup.py): changed is_installed() to use install_if_necessary=False so that a missing Git LFS immediately raises GitLfsSetupError with a clear install hint, instead of stalling on a conda install call.
- **Docker Desktop socket fix** (ersilia/utils/cache.py): added set_docker_host() before docker.from_env() in _remove_container_if_exists(), which was the only Docker SDK call that bypassed the host resolution already used in __init__.
- **Multi-user Docker image protection** (ersilia/utils/docker.py, ersilia/hub/pull/pull.py, ersilia/hub/delete/delete.py, ersilia/db/environments/managers.py): after pulling or building a Docker image, ersilia now stamps it with a ersilia.user.id={uid} Docker label. Delete operations check this label and abort with a clear message if the image was fetched by a different OS user, preventing one user from accidentally removing another user's models on a shared machine.
- **DOI validation for peer-reviewed publications** (ersilia/hub/content/base_information_validator.py, ersilia/publish/test/services/checks.py): added is_valid_doi() to BaseInformationValidator which checks that the publication URL is a valid https://doi.org/ link. This is enforced in _check_model_publication() when the publication type is "Peer reviewed".

**Status**

All four fixes are implemented and tested locally. New unit tests added in test/test_setup_requirements.py and test/test_docker.py covering the Git LFS error path and all Docker ownership scenarios (label match, label mismatch, no label for backward compatibility, dangling image cleanup).

**To do**


Related to #1870 #1847 #1807

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2422df8852f7`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
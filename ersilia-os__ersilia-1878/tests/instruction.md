# Issue

**Title:** Update ersilia API

## Description

Thank you for taking your time to contribute to Ersilia, just a few checks before we proceed
- [x] Have you followed the guidelines in our [Contribution Guide](https://github.com/ersilia-os/ersilia/blob/master/CONTRIBUTING.md)
- [x] Have you written new tests for your core changes, as applicable?
- [x] Have you successfully ran tests with your changes locally?

## Description

This PR updates the ersilia API (create_api.py) to:
- Check if docker is running when fetching models if no source is defined
- Return True if fetch/close/delete succeeds (and False if fetch/close/delete fails)
- Return information on where the model is served if serve() succeeds (it'll throw a RuntimeError if it fails to serve)
- Docs updates (including adding information on running tests locally) 

The linter (`ruff format`) also made changes to these files, but the functionality should be the same:
- `ersilia/cli/commands/__init__.py`
- `ersilia/db/environments/managers.py`
- `ersilia/hub/content/base_information_validator.py`
- `ersilia/hub/delete/delete.py`
- `ersilia/utils/docker.py`

Is this pull request related to any open issue? If yes, replace issueID below with the issue ID
N/A

------------------
## Testing
Ran `pytest -v`
<img width="1173" height="85" alt="image" src="https://github.com/user-attachments/assets/ae492803-906e-4f0b-bb5b-e7ac50bd8548" />

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c6823cfd81dd`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
# Issue

**Title:** hotfix: skipping zairchem models in the catalog command

## Description

This pull request introduces support for excluding certain models managed by ZairaChem from the list of Docker images in the Ersilia catalog. The changes add a new directory reference and logic to read a service file that lists models to be excluded. The most important changes are grouped below:

**ZairaChem integration:**

* Added a new constant `ZAIRACHEM_DIR` to `ersilia/default.py` to reference the ZairaChem directory in the user's home folder.
* Updated imports in `ersilia/hub/content/catalog.py` to include `ZAIRACHEM_DIR`.

**Model exclusion logic:**

* Implemented `_read_zairachem_service_file` method in `ersilia/hub/content/catalog.py` to read a list of model IDs from `service.txt` in the ZairaChem directory.
* Modified `_model_ids_in_docker` to exclude models listed in the ZairaChem `service.txt` file from the Docker image list.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `67c7cedaae43`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
# Issue

**Title:** fixed getting run_columns directly from docker container

## Description

This pull request introduces improvements to the process of copying the `run_columns.csv` file from Docker containers and updates some notebook code for consistency. The most significant change is the refactoring of the Docker file copy logic to be more robust and maintainable, while the notebook updates focus on minor formatting corrections.

**Docker file copy logic improvements:**

* Refactored the `_cp_col_from_container` method in `ersilia/utils/docker.py` to use a more reliable approach for locating and copying `run_columns.csv` from the Docker image, replacing the previous shell-based logic with Python and JSON parsing. It now raises an exception if multiple versions are found and uses a dedicated `cp_from_image` method for copying.
* Updated the `copy_column_file` method in `ersilia/hub/fetch/lazy_fetchers/dockerhub.py` to specify the exact path for `run_columns.csv` and use the correct image tag, with added logging for better traceability.

**Notebook formatting corrections:**

* Fixed inconsistent quotation marks in the DataFrame column selection in `API Blog Demo.ipynb` and `API_organic_solubility.ipynb` for improved readability and code style consistency. [[1]](diffhunk://#diff-18975edbff38968dc8b854b8dd7f7b4a863c49f29e65704d88de4199351c4c0fL102-R102) [[2]](diffhunk://#diff-0316807a7bcdff26915ac572a9ee5b407fd9b461dfdf10870d405c4527641b08L123-R123)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9bc7de52cc4b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
# Issue

**Title:** Loosen python and rdkit restrictions in the environment file.

## Description

I have loosened the restrictions in the `environment.yml` file to support `python<=3.10`, `rdkit<=2022.03`. This is especially important given that python 3.7 has reached end of life. By supporting python 3.10, dockstring will stay supported until 3.10 reaches end of life in October 2026. I updated the README with new instructions for installing the right versions of the required packages.

I have tested that the dataset matching tests pass with the updated versions of each package. However, it looks like `rdkit=2022.03.5` is the highest `rdkit` version where the tests pass. My guess is that they changed some aspect of conformer generation.

Finally, to reflect the looser restrictions I removed the check which raised a warning if `rdkit2021.03` was not installed.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6d0a5897f80b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
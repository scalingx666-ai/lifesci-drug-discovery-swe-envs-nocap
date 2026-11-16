# Issue

**Title:** Uv setup mchip

## Description

1. There’s a different version of tensorflow for macOS (updated in pyproject.toml)
2. `VIRTUAL_ENV`​ is apparently the incorrect flag for the two environment .sh files, so I changed it to `UV_PROJECT_ENVIRONMENT​`. Otherwise, instead of `.venv-<platform>​`, a new folder is created just called `.venv`​ and all the packages are installed there instead. 
3. Installing AMPL afterward without `--no-deps​` reinstalls the wrong version of torch for me. So I changed it to `uv pip install -e . --no-deps`​, and added that command in the sync .sh file for convenience (also updated readme)
4. I created an mchip lock file too.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `65bcfd210ccf`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
# Issue

**Title:** Update Google Colab exception to catch ImportError

## Description

@cbouy For cases where the module google exists, but colab is not installed, an ImportError is raised instead of a ModuleNotFoundError. Updating the catch to include that error. 

Encountered this when running mols2grid on streamlit. This fix solved the issue.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `849cf49a105b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
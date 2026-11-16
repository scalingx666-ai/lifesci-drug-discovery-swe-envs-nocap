# Issue

**Title:** Fix Python 3.10 type checking

## Description

Fixes the Regular Action, specifically the [typecheck in Python 3.10](https://github.com/emdgroup/baybe/actions/runs/33483570142/job/99778572153)

- Two independent problems that only surface in Python 3.10. For pre-commit reasons they had to be committed as one atomic commit
- `ExceptionGroup` import
  - Previously we made a `try`-`except` shenanigans for the `ExceptionGroup` import to account for it not being avaialble in Python 3.10
  - On 3.10 pyrefly does not realize the access to the unavailable `ExceptionGroup` in the try block is intentional to trigger the exception
  - But since `exceptiongroup` is a default dependency of the package anyway we can just always import it normally, it automatically refers to either the back port or the actual object
- Import of beta prior from botorch
  - This is only relevant in 3.10 because the highest available botorch verison does not have this prior avaialble there
  - There is an already existing preset that avoids the import happening in that case, but pyrefly is not able to see this as imports are assessed statically
  - This is usually a situation for an `ignore` comment. But this would be flagged as `unused ignore` in higher Python version 
  - Hence, I went for the slightly more creative solution with impor_module

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `610c45954ba1`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
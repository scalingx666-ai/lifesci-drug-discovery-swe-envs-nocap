# Issue

**Title:** Added --wall, --wall-xl, and --wall-xxl options

## Description

Added the option `-wall`, `-wall-xl`, and `-wall-xxl` to the code at request of @drmewes
These options add a wall potential to the metadynamic simulations, similar to the `-nci` option, but without changing any other settings. the `xl` and `xxl` variants scale the potential axes by a factor of `1.5` and `2.0` respectively. For other sizes the `-wscal` option can be used.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0ce972cc3c7a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
# Issue

**Title:** QCElemental Integration

## Description

We have added a specific `to_string` option for nglview which provides a higher quality interface and reduces dependancies. I have also corrected the name to reflect our common case.

In the docs you name this function `show_qcelementary`, but I couldn't find where to edit them.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `971aeda5e6fa`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
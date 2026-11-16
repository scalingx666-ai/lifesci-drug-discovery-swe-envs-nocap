# Issue

**Title:** Fix gmx execution

## Description

This solves #17 and add new functionalities. Main changes are:

- All execution of `gmx`'s commands are through `bindflow.utils.tools.gmx_command` which allow to load dependencies for the proper function of `gmx`.
- `bindflow.utils.tools.run`  and `bindflow.utils.tools.gmx_command` accept an input command to pipe with the keyword `stdin_command`.
- Adding of helper functions.
- Adding multithreading for mmpbsa analysis.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `57c2f345049a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
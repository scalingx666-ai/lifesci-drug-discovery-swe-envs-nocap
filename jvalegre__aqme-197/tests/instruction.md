# Issue

**Title:** fix "folder_count" referenced before assignment

## Description

This exception is raised in aqme.utils.check_run function when "w_dir" path has "failed" in at least one of its directories.

How to reproduce:
- Create a directory containing "failed" : /home/my_name/testing_molecule_xyz/failed_results
- Move into it
- Run for e.g. an optimization+correction that are know to succeed
- `check_run()` will detect "failed" and not "run_"; therefore will enter the first if branch that leads to the exception.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `68d2ea9a1b5c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
# Issue

**Title:** Implement combined phonon band structure and dos plotting

## Description

Added a `--dos-file` option to `sumo-phonon-bandplot`, which expects a _total_dos.dat_ from Phonopy.
The colour is hard coded and the aspect ratio is not automatically corrected.
Also, only total dos is plotted rather than partial DOS.

Implemented by @ajjackson and @zccaayo.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c8e6705f38e6`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
# Issue

**Title:** Finishing implementing DOS to sumo-phonon-bandplot

## Description

Added a `--dos-file` option to `sumo-phonon-bandplot`, which expects a *total_dos.dat* from Phonopy. 
The colour is hard coded and the aspect ratio is not automatically corrected. 
Also, only total dos is plotted rather than partial DOS.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ce541df7a668`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
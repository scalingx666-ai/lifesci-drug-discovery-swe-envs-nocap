# Issue

**Title:** Protein labelling and m/z calculation

## Description

Hi.
I finished the discussed changes in #35 . The `mw` function now enables to add predefined or manually defined mass shifts at certain amino acids. To compute the mass shifts, I added the `massShift` function.
Also, I added a second function `mz` which enables to calculate mass over charge values for peptides and proteins as detected by mass spectrometers.
Greetings, 
Florian

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `4eede200a47d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
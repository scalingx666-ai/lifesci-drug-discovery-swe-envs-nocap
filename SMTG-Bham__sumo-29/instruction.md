# Issue

**Title:** ENH: --units option for phonon band structures

## Description

Address Issue #28 to add `--units` option to phonon DOS plotter. THz, cm-1, eV and meV are supported. Conversions are performed using the Phonopy unit conversion values. Options are case-insensitive where practical and assigned to correct case in y-axis label.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2bdcc362f063`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
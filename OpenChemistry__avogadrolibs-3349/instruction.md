# Issue

**Title:** Added buddies to lammpsinputdialog.ui

## Description

Part of #3184

### Summary

* Adds `buddy` properties to the field labels in `qtplugins/lammpsinput/lammpsinputdialog.ui` so screen readers announce each field with its label.
* 14 more labels now have a buddy pointing at the field next to them in the grid. Together with the 4 that already had one (Title, Units, Atom Style, Dimensions), that brings the total to 18 of 20 labels.
* Skipped "Boundary" and "Replicate" because each describes a group of three X/Y/Z fields.
* The two "Temperature" labels (thermostat and initial velocities) are both announced as "Temperature"; telling them apart would mean changing label text, which I left alone because of the string freeze.

### Testing

Built on Windows (MinGW, Qt 6.10.2), opened Input in LAMMPS and tabbed through the fields with Narrator. Fields are now announced with their label; for example: "Time Step, spin button, 2".

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `09bb4c16542f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
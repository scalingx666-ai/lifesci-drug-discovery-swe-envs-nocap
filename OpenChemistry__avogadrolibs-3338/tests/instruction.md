# Issue

**Title:** Added Buddies to openmminputdialog.ui

## Description

Part of #3184 

### Summary

- Adds `buddy`  label to the field labels in `qtplugins/openmminput/openmminputdialog.ui` so screen readers announce each field with its label.

- 30 labels now have a buddy pointing at the field next to them in the grid.

-  Skipped "Reporters:" and "StateData options:" because each describes a group of check boxes, which carry their own text.

### Testing
  
Built on Windows (MinGW, Qt 6.10.2), opened OpenMM 
Script Builder, and tabbed through the fields with Narrator. Fields are now
announced with their label; for example: "Forcefield, combo box, AMBER96".

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1a692d6c8e27`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
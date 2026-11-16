# Issue

**Title:** Added Buddies to Calculation Setup

## Description

Part of #3184

### Summary

- Adds `buddy` properties to the field labels in `gamessinput/gamessinputdialog.ui`, `forcefield/forcefielddialog.ui`, `constraints/constraintsdialog.ui`, `apbs/apbsdialog.ui`, and `yaehmop/banddialog.ui` so screen readers announce each field with its label.
- `gamessinputdialog.ui`: finished the remaining 3 labels (`"MAX SCF"`, `"CONV THRESH"`, `"Filename Base:"`).
- `forcefielddialog.ui`: all 4 labels now have a buddy.
- `constraintsdialog.ui`: `"Type:"` and `"Value:"` now have buddies. `"Atom Indices:"` was skipped because it describes four spin boxes.
- `apbsdialog.ui`: all 3 labels now have a buddy.
- `banddialog.ui`: the remaining 3 labels now have a buddy.
- Left all existing label text unchanged because of the string freeze.

### Testing

Built on Windows (MinGW, Qt 6.10.2), opened the GAMESS input, Geometry Optimization Parameters, Constraints, APBS, and Yaehmop band structure dialogs, and tabbed through the fields with Narrator. All 15 new buddied fields are now announced with their labels before their control types and values.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e19c8cae8221`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
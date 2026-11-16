# Issue

**Title:** Added buddies to cp2kinputdialog.ui

## Description

Part of #3184

### Summary
* Adds `buddy` properties to the field labels in `qtplugins/cp2kinput/cp2kinputdialog.ui` so screen readers announce each field with its label.
* 14 more labels now have a buddy pointing at the field next to them: Filename Base and Functional on the Basic Setup tab, the 5 fields on the MM tab, and the 7 fields on the QM tab. Together with the 4 that already had one (Title, Calculate, Method, Basis set), all 18 labels in the dialog now have a buddy.
* The LSD checkbox is still announced by its own text ("TRUE, check box") rather than "LSD", because Qt names checkboxes from their own text instead of the buddy label. Fixing that would mean adding an accessible name or changing the checkbox text, which I left alone because of the string freeze. The buddy still moves focus to the checkbox when the label is clicked.
* The MM and QM labels use CP2K keyword names (e.g. "EPS SCF", "OT T MINIMIZER"), so that's what gets announced; I left the label text alone for the same reason.

### Testing

Built on Windows (MinGW, Qt 6.10.2), opened Input in CP2K and tabbed through the fields with Narrator. Fields are now announced with their label; for example: "Functional, BLYP, combo box, collapsed".

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `09bb4c16542f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
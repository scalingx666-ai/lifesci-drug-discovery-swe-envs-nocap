# Issue

**Title:** Added Buddies to Everything else

## Description

Part of #3184

### Summary

- Adds `buddy` properties to 9 field labels across `insertfragmentdialog.ui`, `pqrwidget.ui`, `condadialog.ui`, `configurepythondialog.ui`, and `symmetrywidget.ui` so screen readers announce each field with its label.
- Skipped `textLabel` in `condadialog.ui` and `configurepythondialog.ui`, `pointGroupLabel` in `symmetrywidget.ui`, and `formulaDisplay`, `pngPreview`, and `label_5` ("Formula:") in `pqrwidget.ui` because they only display information and have no focusable field to point at.
- Made no changes to `packagemanagerdialog.ui` because its only field (`searchEdit`) has no visible label; its other labels only display plugin information.
- Left all existing label text unchanged because of the string freeze.

### Testing

Built on Windows (MinGW, Qt 6.10.2), opened the Insert Fragment, Import From PQR,
Python Settings, and Symmetry dialogs, and tabbed through the fields with Narrator.
All 9 new buddy fields are now announced with their labels before their control
types and values.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `aa2198141f73`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
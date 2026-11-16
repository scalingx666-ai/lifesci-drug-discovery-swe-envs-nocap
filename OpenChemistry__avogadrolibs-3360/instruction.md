# Issue

**Title:** Added Buddies to manipulatewidget.ui

## Description

Part of #3184

### Summary

- Adds `buddy` properties to the field labels in `qtplugins/manipulator/manipulatewidget.ui` so screen readers announce each field with its label.
- 8 of the 9 `QLabel`s now have a buddy pointing at the field they describe: `X`, `Y`, and `Z` link to `xTranslateSpinBox`, `yTranslateSpinBox`, and `zTranslateSpinBox`; `"Rotate around:"` links to `rotateComboBox`; `X-axis`, `Y-axis`, and `Z-axis` link to `xRotateSpinBox`, `yRotateSpinBox`, and `zRotateSpinBox`; and `"Move:"` links to `moveComboBox`.
- Skipped `"Translate by:"` because it is a group heading above the three `X`/`Y`/`Z` translation spin boxes.
- Left all existing label text unchanged because of the string freeze.

### Testing

Built on Windows (MinGW, Qt 6.10.2), selected the Manipulate tool (`Ctrl+5`) to open its tool panel, and tabbed through the fields with Narrator. All 8 fields are now announced with their labels before their control types and values.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `06b2e747c2e7`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
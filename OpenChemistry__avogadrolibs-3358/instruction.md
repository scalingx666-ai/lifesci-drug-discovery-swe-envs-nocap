# Issue

**Title:** Added buddies to unitcelldialog.ui

## Description

Part of #3184

### Summary

- Adds `buddy` properties to the field labels in `qtplugins/crystal/unitcelldialog.ui` so screen readers announce each field with its label.
- All 8 labels in the Unit Cell Editor now have a buddy pointing at the field they describe: A, B, C, α, β, and γ link to their spin boxes, and "Cell Matrix:" and "Fractional Matrix:" link to the matrix text boxes below them.
- `importcrystaldialog.ui` needed no change: its only label ("File extension for Open Babel conversion") already has `edit_extension` as its buddy, and the text box for the pasted crystal data has no label.
- `supercelldialog.ui` has none of its labels because it names a single field: "Minimum" and "Maximum" are column headings, each "A/B/C range:" label covers both a minimum and a maximum spin box, and the rest is hint or warning text.

### Testing

Built on Windows (MinGW, Qt 6.10.2), opened Crystal, opened Edit Unit Cell, and tabbed through the fields with Narrator. Each field (A, B, C, α, β, γ, Cell Matrix, and Fractional Matrix) is now announced with its label before its type and value.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `06b2e747c2e7`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
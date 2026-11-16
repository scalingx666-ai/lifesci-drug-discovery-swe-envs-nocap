# Issue

**Title:** Add label buddies to surface dialogs

## Description

Addresses the `qtplugins/surfaces/` portion of #3184.

## Changes

- Connect the eight field labels in `surfacedialog.ui` and `orbitalwidget.ui` to their primary input controls.
- Preserve all existing label text and translated strings.
- Keep the diff limited to new Qt label metadata.

## Validation

- `xmllint --noout` passed for both UI files.
- Qt 6 `uic` compiled both UI files successfully.
- The generated headers contain all eight expected `setBuddy()` connections.
- The full Avogadro build and native screen-reader testing were not completed locally.

## AI assistance

I used Codex to inspect the repository structure, explain the Qt UI XML, suggest focused validation commands, and review my diff. I used Claude's course plan-check and PR gate to compare the plan and submission package with the issue and repository requirements. I selected and typed every XML change, personally ran the validation commands, and verified every changed line.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `eda6844c1306`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
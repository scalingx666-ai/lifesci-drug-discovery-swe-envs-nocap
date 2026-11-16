# Issue

**Title:** Add label buddies to the spectra dialog

## Description

Addresses the spectra-dialog portion of #3184.

### Changes
- Add 13 label buddy connections to individually labeled controls.
- Preserve all translated strings and other UI content.
- Leave labels describing groups of controls unchanged.

### Validation
- Qt UI compilation passed.
- An isolated Qt check verified all 13 buddy connections.
- Full Avogadro build and native screen-reader testing remain outstanding.
- The editable font-size control and color buttons still need native accessibility verification.

### AI assistance
The XML changes and validation tooling were prepared with assistance from AI (Codex). Feedback is welcome on the implementation and the outstanding accessibility testing.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f359a7bfb9e8`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
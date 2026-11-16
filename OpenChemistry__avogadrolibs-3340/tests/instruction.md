# Issue

**Title:** Add label buddies to the insert polymer dialog

## Description

Screen readers now announce the A/B/C unit buttons, repeat style, total length and tacticity fields with their labels. The Structure, Name and Repeats labels each describe a row of three fields and are left without a buddy.

Part of #3184.

Checked: not checked with a screen reader or Accessibility Inspector (I couldn't build Avogadro here). Each buddy name matches a widget in the same file.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `55ecd967dfa8`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
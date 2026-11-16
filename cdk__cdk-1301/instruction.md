# Issue

**Title:** This calculations should be on "visible" neighbours only. If we contr…

## Description

…act -NO2 for example we go from 3 equally spaced bonds to only 1 and the alignment here should trigger.

Not a massive issue but a regression I introduced, would be nice to be able to test this code better but rendering/visualisation is always tricky since a small change in pixels for example may be fine.

before:
<img width="63" height="53" alt="tmp-old" src="https://github.com/user-attachments/assets/a0dd14a0-1f6b-4523-a931-0e578eb8413c" />

after:
<img width="63" height="53" alt="tmp" src="https://github.com/user-attachments/assets/9318268b-c32b-47b8-9f34-37ec1dafe4d2" />

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3bc6efe84119`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
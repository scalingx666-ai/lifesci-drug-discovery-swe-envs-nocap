# Issue

**Title:** chore: stop tracking DESIGN.md and PRODUCT.md

## Description

Removes DESIGN.md and PRODUCT.md from version control and adds them to .gitignore. They stay as local design notes, the same as design/ and .impeccable/.

No code changes.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `716d2b1296b1`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
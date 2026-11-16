# Issue

**Title:** mmtf optimization issue

## Description

Writing a mmtf file of a big molecule is taking a lot of time abnormally.

On line 593 of src/formats/MMTF.cpp there is the line :
`auto positions = frame.positions();`

This affectation make a copy of the whole position vector instead of just got a reference.
Because this affectation is called for every residue, it dramatically slow down the writing process.

Changing it to
`const auto& positions = frame.positions();`

will use a reference assignment and correct the optimization issue.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `501b7cbb7678`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
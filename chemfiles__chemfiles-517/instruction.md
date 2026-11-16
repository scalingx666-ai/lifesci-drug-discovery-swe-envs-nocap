# Issue

**Title:** Add support for XTC format for gigantic systems

## Description

.

I faked a test XTC file for reading, but properly testing writing is really hard because single frames can become rather large.
Instead of testing writing of the new XTC format directly, the underlying compression functions are tested in the XDR file tests.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c4be017334ca`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
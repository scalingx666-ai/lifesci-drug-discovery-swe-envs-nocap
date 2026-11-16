# Issue

**Title:** This fixes a problem with the ordering of &.

## Description

This fixes a problem with the ordering of &. The reason was that in the getSphereCode method, so pretty much at the end, after all sorting etc., the atom symbol is replaced with an & for ring closures. At the same time, looking at rankedSymbols/symbolRankings, it is clear that the & is supposed to come after all the symbols. This can cause trouble with symmetries, a test case is added. I also had to modify some other test cases since they simply had wrong hose codes. There were spheres described like "&C" which clearly should not happen, it must be "C&". I have also used the legacy mode to make sure the old hose codes don't change.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d7d1c3dcd89e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
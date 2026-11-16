# Issue

**Title:** Add 'aaSequence' to get all amino acids uppercase single-char names, fix #29

## Description

Hi @dosorio,

As promised, I've added `aaSequence`, both function and tests.

Sadly, I could not test, as I could not build the package. Because there is no CI on your repo either, you will have to check manually yourself. I am experience adding Travis CI to repos, but I am unsure if you'd be open for that.

Cheers, Richel

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e3a471ebc71b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
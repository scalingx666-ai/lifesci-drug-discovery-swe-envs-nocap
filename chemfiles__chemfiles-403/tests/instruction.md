# Issue

**Title:** Guarantee fixed iteration order over properties

## Description

Properties are now stored inside a `std::map`, which guarantee a fixed iteration order over them (they will be sorted according to the property name). This removes a source of non determinism in code and written files

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5ab49526dd00`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
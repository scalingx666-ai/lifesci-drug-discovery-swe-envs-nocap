# Issue

**Title:** feature/ipickering/similarity cpp extensions

## Description

- **Preliminary C++ implementation**
- **Add dummy impl of C++ extensions (SLOW)**
- **Update cpp extensions to actually be faster than birch**
- **Ignore profile files**

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b51d1308a182`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
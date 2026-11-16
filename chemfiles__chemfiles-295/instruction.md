# Issue

**Title:** Improve speed of MMTF parsing for global bonds

## Description

Before:

```
$ time ./mmtf
[chemfiles] MMTF Writer: atom name 'C23456' is too long for MMTF format, it will be truncated
[chemfiles] MMTF Writer: atom type 'HuuuuH' is too long for MMTF format, it will be truncated
===============================================================================
All tests passed (117 assertions in 2 test cases)

./mmtf  785.46s user 0.25s system 99% cpu 13:05.78 total
```

After:
 ```
$ time ./mmtf
[chemfiles] MMTF Writer: atom name 'C23456' is too long for MMTF format, it will be truncated
[chemfiles] MMTF Writer: atom type 'HuuuuH' is too long for MMTF format, it will be truncated
===============================================================================
All tests passed (117 assertions in 2 test cases)

./mmtf  1.79s user 0.28s system 99% cpu 2.067 total
```

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `efacbf09230e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
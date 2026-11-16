# Issue

**Title:** Compatibility with pandas 1

## Description

Dear Oskar Weser,
I have:
1. a) removed the "by" from pd.sort_index(..., sort_remaining=by). One could check the pd version and based on that call the function differently, but I deem it superfluous as "by" was always left equal to "None" (at least as far as I saw).
b) This functions is called by "zmat.get_cartesian()" which is already tested, so no additional test is needed
2. some tests were failing because of leading spaces (e.g. " O 0.0 0.0 0.0" instead of "O 0.0 0.0 0.0"). I think this also depends on package versions and the test should accept both. I creat both versions and assert the result matches either.
3. I propose (feel free to discard) a cartesian.read_string() for users that may not be familiar with StringIO. 

Best, NR

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c58eac51e00c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
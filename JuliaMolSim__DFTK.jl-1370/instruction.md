# Issue

**Title:** Fix NLCC force missing enforce_real!

## Description

~~This is one possible fix, but upon closer inspection the entire `enforce_real!` function is very suspicious. Let's discuss in #1369.~~ This is the correct fix, it's just that `enforce_real!` is misnamed (should be renamed: ).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `14bbd6318063`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
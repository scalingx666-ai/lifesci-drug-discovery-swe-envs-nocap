# Issue

**Title:** docs: deduplicate include/exclude_half.life via @inheritParams

## Description

Document exclude_half.life/include_half.life in a single location (PKNCAconc) and inherit them in pk.nca.interval via @inheritParams, so the description lives in one place. The shared text is phrased to cover both forms: a logical column name in PKNCAconc(), or the logical vector itself. Regenerate man pages (the two topics now share identical argument text).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0e8caa378957`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
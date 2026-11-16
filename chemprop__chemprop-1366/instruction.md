# Issue

**Title:** V_ds is never None in multi

## Description

I noticed the type hint for V_ds here is `Iterable[Tensor | None]`, but we check `if V_ds is None`. The relevant line in collate.py is `[tb.V_d for tb in tbs]`, so the type hint is correct. This means our if statement is always false and can be removed.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5e8ba3f9a5b8`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
# Issue

**Title:** added callable as possible row indexer

## Description

allow indexing with a query function such as
```python3
molecule.loc[lambda m: m.atom != "H", :]
```
to enable a fluent interface.

(This was already possible at runtime, but not encoded in the type system.)

---------------------------------------------------------------------

Clean up after new test.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3584ac2ad733`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
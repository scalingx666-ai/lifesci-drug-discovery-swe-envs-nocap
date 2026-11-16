# Issue

**Title:** add type definitions (.d.ts)

## Description

Added TypeScript type definitions to resolve #36  
Based on definitions found in minilib.h and jswrapper.cpp in the rdkit/Code/MinimalLib repo.

Remaining todos:

- [x] writing typescript usage examples  (TODO @adam-of-barot )

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d9efa9232d96`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
# Issue

**Title:** Adding a delimiter to save the output results of fragmentation

## Description

Adding a delimiter to save the output results of rdMMPA.FragmentMol in fragmentation.py. This might be required when certain smiles contain ',' in the pattern, and thus ',' cannot be used as a delimiter. Characters like '\t' can be used as an argument in that case. The same delimiter must be provided as an argument to frag_to_env_mp.py also.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `562f6040bb75`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
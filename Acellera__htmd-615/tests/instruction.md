# Issue

**Title:** Implements versioning on LSF (9 and 10)

## Description

Updated ngpus to work with the new version and implements the new gpu_options
Updates the docstring
Depends on Acellera/protocolinterface#5 and  
@stefdoerr you need to review Acellera/protocolinterface#5 first :)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c9c6b791fc68`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
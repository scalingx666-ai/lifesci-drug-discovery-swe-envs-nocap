# Issue

**Title:** Add reference for RPBE parameters

## Description

Despite of what the comment said, RPBE parameters are from the GMTKN55 paper (SI, page S6, Table S3). .

Unrelated, but for future reference: The `a1` parameter for RPBE-D3(BJ) is rather small, which may lead to too weak damping and large dispersion energies. This seems to mainly affect larger atoms (found for a system with 64 Co atoms). GMTKN55-like chemistry seems unaffected since RPBE-D3(BJ) performs similarly to PBE-D3(BJ) and no outliers are reported.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6004cfd62ad2`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
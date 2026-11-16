# Issue

**Title:** Add more D3(BJ) parametrizations

## Description

DSD-PBEP86-D3(BJ) from 10.1039/c1cp22592h has name `dsdpbep86_2011`
DSD-BLYP-D3(BJ) from 10.1002/jcc.23391 has name `dsdblyp_2013` since it has another set of parameters already.

~~dRPA75-D3(BJ) from MRCC has name `drpa75_mrcc`
SCS-dRPA75-D3(BJ) from MRCC has name `scsdrpa75_mrcc`~~

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `8bf83492c035`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
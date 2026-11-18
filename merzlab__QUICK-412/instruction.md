# Issue

**Title:** QUICK 25.03 Build System Updates

## Description

This PR backports recent AmberTools build system updates and bumps the supported CUDA versions (and GCC compatibilty checks) in light of recent releases.

Notes / Limitations:
- Tested up to CUDA v12.6.3 + GCC v13.3.1 on my personal systems and up to CUDA v12.4 + GCC v12.3.0 on the MSU HPCC clusters (CUDA v12.8.0 / v12.8.1 are future work for my setup).
- Recent AmberTools changes do not address #391.  Hence, this still needs to be addressed.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0910114ee2f6`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
# Issue

**Title:** Add a warning when the NLCC causes negative Fermi hole curvature

## Description

As discussed in 

FYI the related LibXC code is: https://gitlab.com/libxc/libxc/-/blob/devel/src/work_mgga_inc.c?ref_type=heads#L58 and similar below for the second spin channel.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c6d1e83a59e2`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
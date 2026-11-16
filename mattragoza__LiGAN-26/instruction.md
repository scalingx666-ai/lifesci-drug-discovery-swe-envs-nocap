# Issue

**Title:** Expose GNINA executable

## Description

The path to the GNINA executable is currently hard-coded:
https://github.com/mattragoza/liGAN/blob/6842f35e39cac2cd9d8b308c978ec11d2f0f50e2/liGAN/molecules.py#L21

This PR allows to define the GNINA executable as an environment variable (and falls back to the original path by default).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6842f35e39ca`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
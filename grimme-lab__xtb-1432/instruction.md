# Issue

**Title:** Preserve atoms in fragmented GFN-FF Hessians

## Description

Fragment grid bounds included unused zero-initialized center entries, making the partition depend on the coordinate origin. For translated clusters (like in #1286 where many of the waters were displace 300 Angstroms away from the origin) this could place many disconnected molecules in one oversized block; the splitter for overly large groups assumes they are fully connected, which leads to it only retain the two endpoint components (disconnected waters), leaving the atoms from all the other waters without Hessian modes.

This change computes bounds based on active small fragments, caps merged blocks at the fragment size limit, and ensures already group fragments are skipped.  We now check that every atom belongs to exactly one fragment and fall back to full diagonalization if that check fails.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a45f05d39726`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
# Issue

**Title:** Optimize AtomicNonlocal term for the GPU

## Description

This PR optimizes the `AtomicNonlocal` term instantiation and forces for the GPU. The same principles as #1163 and #1262 are applied. The largest performance impact is felt in stress and response calculations, when Duals are involved. However, since the `AtomicNonlocal` term was never fully ported to the GPU, standard SCF and forces calculations are also accelerated.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5dc3e5d5609b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
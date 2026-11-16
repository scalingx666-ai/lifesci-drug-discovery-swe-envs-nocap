# Issue

**Title:** Fix mol weight float prop types

## Description

The PubChem PUG REST API changed at some point to supply molecular weight, exact mass, and monoisotopic mass as string values instead of float values. This is presumably just to maintain precision during serialization, so I think we are safe to cast back to float, to maintain the previous behavior.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `16850b6f4f32`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
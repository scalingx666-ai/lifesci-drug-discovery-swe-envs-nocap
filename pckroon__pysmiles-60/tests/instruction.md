# Issue

**Title:** ENH: broaden SMILES handling to match RDKit

## Description

* Related to a small part of 

* One of the problematic SMILES permutations that RDKit considers isomorphic with a more canonical SMILES was not handled properly by `pysmiles`. This is a small shim (via regex) and regression test to start enforcing equivalence for at least this one extra permutation.

* It is possible to generate many more scrambled/randomized SMILES permutations in RDKit, but for now this one extra permutation is the closest to what the chemists provided me, so is of most interest to me at least.

* In local testing I don't see any problems, altough `tests/test_hypothesis.py::Tester::runTest` seems to fail for me even on `master` (decent chance it could be my recent version of `hypothesis`, which can change case generation by version).

------------------

AI usage disclaimer: I did ask an LLM to help me draft the regex for moving the ring termination number relative to the parenthetical double bond. The regression test I wrote myself based on in house needs.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c64f7f6638b6`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
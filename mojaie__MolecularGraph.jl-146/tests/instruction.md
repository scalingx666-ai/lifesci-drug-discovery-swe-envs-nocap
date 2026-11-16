# Issue

**Title:** Fix name collision in `maximum_clique`

## Description

Graphs v1.14.0 started exporting `maximum_clique`, which is a function that MolecularGraph also exports. The two names collide, which causes problems for MolecularGraph's test suite.

This "fixes" the problem by merging the two functions, having MolecularGraph add new methods to the Graphs function. Currently, this PR should be viewed as a "trial balloon" because there is a major problem: solving the problem this way is piracy. There are several alternatives, including (1) renaming MolecularGraph's function to something else, (2) scoping calls to `MolecularGraph.maximum_clique` in the test suite, or (3) defining a new function in MolecularGraph that calls Graphs' function and then does some post-processing. Let me know your preferred solution and I can implement it.

Because this was introducing piracy, I also took the liberty of adding Aqua tests. Currently this highlights quite a few failures (not just the piracy I introduced), so I marked the test as broken. Fixing these should be the subject of a future PR.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5e015a8580a2`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
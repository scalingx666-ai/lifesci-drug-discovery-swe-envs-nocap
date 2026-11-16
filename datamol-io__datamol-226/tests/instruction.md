# Issue

**Title:** refactor to rdFingerprintGenerator

## Description

## Changelogs
This PR addresses the fingerprint deprecation warnings, see issue #225. 

- Refactoring fingerprint atom pair, rdkit, morgan, topological, and their count fingerprints to FingerprintGenerator.
- `ecfp-count` now use the ECFP-6, to stay consistent.
- added new decorator function `dm.no_rdkit_log` which disable RDKit log for a whole function. 
- set minimum rdkit version to avoid pandas based error for this version of datamol. 

---

_Checklist:_

- [x] _Was this PR discussed in an issue? It is recommended to first discuss a new feature into a GitHub issue before opening a PR._
- [x] _Add tests to cover the fixed bug(s) or the new introduced feature(s) (if appropriate)._
- [ ] _Update the API documentation is a new function is added, or an existing one is deleted._
- [x] _Write concise and explanatory changelogs below._
- [x] _If possible, assign one of the following labels to the PR: `feature`, `fix` or `test` (or ask a maintainer to do it for you)._

---

The `rdFingerprintGenerator.GetCountFingerprint` can be used to compute the count based fingerprint. 
The argument `countSimulation`indicates whether to compute the count fingerprint by bites simulation for computing efficiency. See more in [this blog](https://greglandrum.github.io/rdkit-blog/posts/2021-07-06-simulating-counts.html#topological-torsions). 
I assume in `datamol`, we want to compute the exact count-based fingerprint. Therefore, `countSimulation` should be set to False.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `cc3cc3648d30`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
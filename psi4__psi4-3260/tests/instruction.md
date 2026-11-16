# Issue

**Title:** pin hdf5=1.14.3 and job pool

## Description

## Description
<!-- Provide a brief description of the PR's purpose here. -->

## Dev notes & details
<!-- A bullet-point format description of what this PR does "at a glance."
     Target audience is code reviewers and other devs skimming PRs.
     Should be more technical than user notes. Should never be empty. -->
- [x] the conda 1.14.4 packages aren't setting HDF5_VERSION, which psi4 expects. this pins to 1.14.3 to avoid the error.
- [x] Ninja long has started more files compiling in libmints than it should, resulting in OOM errors. We've been constraining the threads for the whole compile, but job pools can isolate to a portion of libmints files. it'll be trial-and-error to get the cutoffs right. Leaving the azure as Makefiles b/c faster.

## Checklist
- [ ] Tests added for any new features
- [ ] [All or relevant fraction of full tests run](http://psicode.org/psi4manual/master/build_planning.html#how-to-run-a-subset-of-tests)

## Status
- [x] Ready for review
- [x] Ready for merge

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a25e71659d32`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
# Issue

**Title:** Updates for dependencies (especially RDKit and NumPy)

## Description

This PR updates `pdbeccdutils` to work with more recent versions of dependencies, especially RDKit and NumPy. Context is that some aspects of OpenFold, which depends on pbdeccdutils, need newer versions of RDKit. Additionally, the pin to NumPy 1.26 may become a problem; as I understand it, the recommendation is to [drop support for 1.26 in a few months](https://scientific-python.org/specs/spec-0000/).

* f39813293aea6f92ab1c50bc08b2c31608f6baba solves a problem introduced in RDKit 2025. See  for details.
* 38c8dcc984c86db95552814f4a3249e51949077d switches to `np.nan` instead of `np.NaN`, which was removed in NumPy 2.0.
* 9b60cd3a8065c322d8041ee0c90040186b1a3960 updates the lockfile and pyproject.toml to set lower bounds on dependencies.

I haven't added a scheduled GitHub Actions workflow to test against updated versions, although this might be recommended.

.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `618f680010d6`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
# Issue

**Title:** Use wheel for tox testing

## Description

This changes the tox configuration to build a wheel and use that wheel for testing, similar to how we do it in the other addons.

It is important to ensure that the wheel itself is used during testing rather than the `qiskit_addon_sqd` local directory, as the latter will not automatically have the compiled code available.  So, to restore the ability to run `tox -e py` from the root directory of the repository, this PR moves all python source files to a directory called `python`. This is a layout [recommended by the maturin docs](https://www.maturin.rs/project_layout.html#mixed-rustpython-project) and is also the one used by ffsim.  This structure provides the benefits of a [`src`
layout](https://packaging.python.org/en/latest/discussions/src-layout-vs-flat-layout/).

One nice thing about the new directory structure is that many of the lines in `tox.ini` now say `python/` instead of `qiskit_addon_sqd/`. So, if other addons were to adopt this change, then their `tox.ini` files would look even more alike, which could be good for maintainability.

This also bumps the versions of numpy and pyo3 to 0.26.  I cannot remember at this point whether it was absolutely necessary, and if desired I could try to separate out this change.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `19058dbd3a15`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
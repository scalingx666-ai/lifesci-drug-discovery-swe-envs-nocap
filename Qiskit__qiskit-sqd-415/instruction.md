# Issue

**Title:** Require Python 3.11 or later

## Description

Qiskit raised its own minimum supported Python to 3.11 in  where qiskit 2.6 is named as the last release supporting 3.10.  This does the same for sqd.

Python 3.10 itself went end of life on 2026-10-01.

Version knobs: `requires-python`, the 3.10 classifier, `[tool.mypy] python_version`, `[tool.pylint] py-version`, the tox `env_list`, and the Python version in `docs.yml`, `lint.yml`, `test_minimum_versions.yml`, `test_latest_versions.yml`, `test_development_versions.yml`, and `nightly_qiskit_prerelease.yml`.

The `qiskit>=2.0, <3` range is unchanged: 17135 is not in a release yet, so nothing in the supported range requires a newer floor.

No other dependency floors needed raising either.  I pinned every declared minimum with `extremal-python-dependencies pin-dependencies-to-minimum` and ran the suite on 3.11: 63 passed.  Every floor already ships a cp311 wheel.

Two things beyond the mechanical bump:

- The `base_python` pins in the `lint` and `docs` environments are gone.  They date to the initial commit and pinned the then-current minimum rather than expressing a real constraint, so CI's chosen interpreter should decide.
- Dropping those pins lets `lint` resolve a current numpy (2.5.4 here), and that surfaced two separate issues.  `bitstring_matrix_to_integers` needs an explicit annotation, since `np.zeros` with a variable `dtype` is no longer inferable.  Separately, numpy's stubs use PEP 695 `type` statements, which mypy rejects unless it analyzes as 3.12 or later — so `[tool.mypy] python_version` is now 3.12, with a comment saying why it is deliberately ahead of `requires-python`.

That last one is the judgment worth a look.  The alternatives were dropping `python_version` entirely (mypy then follows the interpreter) or restoring the `base_python` pin so an older numpy resolves.  3.12 keeps an explicit analysis target at the cost of the number no longer tracking the supported floor.

`tox -e lint` and `tox -e py311` pass.  I could not run `tox -e docs` locally: `sbd-eigensolver` publishes no wheels and its sdist needs MPI, which my machine lacks.  That is unrelated to this change — it fails the same way on `main`, including on 3.10.

Ruff's `target-version` stays at `py39` here.  Moving it is left to a follow-up PR.

<hr>

This pull request was drafted by Claude Opus 5 under my guidance.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2364dbc61fc7`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
# Issue

**Title:** Expose a __version__ attribute

## Description

`qiskit_addon_sqd` now binds a toplevel `__version__`, read back from the installed distribution metadata so that `pyproject.toml` remains the single source of truth. The attribute is left unbound when importing from an uninstalled source tree.

This matches `qiskit-addon-aqc-tensor` and `qiskit-addon-cutting`, which expose the attribute the same way. The spelling differs: those two use `try`/`except PackageNotFoundError`/`pass`, which this repo's ruff configuration rejects under SIM105, since it enables the full `SIM` ruleset. `contextlib.suppress` is the form ruff asks for here.

<hr>
This pull request was drafted by Claude Opus 5 under my guidance.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `36237720192c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
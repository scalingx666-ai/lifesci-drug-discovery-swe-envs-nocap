# Issue

**Title:** test: check the data files in a built wheel, not just the checkout

## Description

Follow-up to a review comment on #644, and to @crispppp's report in #643.

## The gap

SMACT reads nearly all of its reference data from files under `smact/data` — element data, the oxidation state tables, the Shannon radii, the species embeddings. Those files reach users only if they are declared in `[tool.setuptools.package-data]`.

Nothing in the suite could catch a missing declaration. The `test` job installs the project with `uv sync`, which is an **editable** install, so `smact.data_directory` resolves to the checkout, where every committed file is present whether or not it would ship. Dropping a glob from `pyproject.toml` would leave CI fully green while `pip install smact` produced a package that raises `FileNotFoundError` on first use — which is the shape of the failure the reviewer hit in #643, arriving from the other direction.

## What this adds

`smact/tests/test_packaging.py` checks the data a user actually receives:

- every declared package-data glob still matches at least one installed file;
- each data file that `smact/` reads at runtime is present and non-empty;
- `py.typed` ships, so downstream type checkers see the annotations;
- `Element`, `Species` and the three `doper` embedding tables load, exercising the files through the public API rather than only checking paths;
- the module's own glob list is cross-checked against `pyproject.toml` when running from the repo, so the two cannot drift apart. That check skips when running against an installed package, where `pyproject.toml` is absent.

The module deliberately has no fixture-file dependencies: `smact/tests/files/` is not declared as package data, so it does not ship, and a wheel cannot run the rest of the suite.

`.github/workflows/packaging.yml` builds a wheel, installs it into a bare environment, and runs that module from a directory that does not hold the source tree, so `import smact` resolves to the wheel and not to the checkout.

Two notes on how it is wired:

- It triggers on `pull_request`, not `pull_request_target` like `SMACT CI`. It needs no secrets, and `pull_request` takes the workflow definition from the pull request itself — so this job runs on this PR, rather than only becoming live after merge.
- `publish-to-pypi.yml` now depends on it, so a wheel missing its data files cannot be published. The release workflow previously ran the suite against the checkout and then built, which had the same blind spot.

## Verification

- Built a wheel, installed it clean, ran the module from a temp directory: 29 passed, 1 skipped (the `pyproject.toml` cross-check, correctly skipped against an installed package).
- Dropped `"data/*.json"` from `package-data` and rebuilt from a clean tree: the wheel run fails on the `data/*.json` glob and on both affected files, while the editable-install suite stays green — i.e. the guard catches exactly what it is meant to.
- Run from the repo with that same change, the `pyproject.toml` cross-check fails too.
- Full suite on this branch: 310 passed, 2 skipped. `pre-commit run --all-files` clean.

One thing worth knowing for anyone reproducing this locally: `uv build` reuses a stale `build/lib`, so data files from an earlier build can persist into a later wheel. `rm -rf build SMACT.egg-info` before building, or the check will pass against files your working tree no longer has. CI checks out fresh, so it is unaffected.

<!-- This is an auto-generated comment: release notes by coderabbit.ai -->
## Summary by CodeRabbit

* **New Features**
  * Added automated validation for built wheels and installed distributions.
  * Verified that required runtime data, type information, and element and species data are included and load correctly.
  * Improved confidence that installed packages provide the same functionality as source installations.

* **Chores**
  * Updated the release workflow to complete packaging validation before building distributions.
  * Packaging checks now run for pull requests, pushes to `master`, and reusable workflow calls.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3512ebb109f7`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
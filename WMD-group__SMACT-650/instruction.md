# Issue

**Title:** deps: clear the vulnerable transitive pins in uv.lock

## Description

Clears all 11 open Dependabot alerts (6 high, 4 moderate, 1 low).

## Context first

Every one of them is transitive, and none is reachable from a default `pip install smact`:

| package | alerts | how it is reached |
|---|---|---|
| GitPython | 9 (6 high, 3 moderate) | `smact[property_prediction]` → `aviary-models` → `wandb` → `gitpython` |
| Pygments | 1 (low) | sphinx, pytest, ipython — docs and dev tooling |
| setuptools | 1 (moderate) | build tooling |

Worth stating plainly in the JOSS thread, since "Good practices" is one of the unchecked review boxes: the alert count on the Security tab does not describe what a user installs.

## The bumps

```
gitpython  3.1.54 -> 3.1.61   (advisories patched at 3.1.58)
pygments   2.19.1 -> 2.21.0   (patched at 2.20.0)
setuptools 78.1.0 -> 84.0.0   (patched at 83.0.0)
```

**setuptools could not move on its own.** Both 83.0.0 — the first patched release — and 84.0.0 drop `pkg_resources`, which `pybtex` 0.24.0 imports at module scope. That breaks `emmet.core.provenance`, so `mp_api.client.routes.materials` fails to import and `test_utils.py` will not collect:

```
pybtex/plugin/__init__.py:26: in <module>
    import pkg_resources
E   ModuleNotFoundError: No module named 'pkg_resources'
```

`pybtex` 0.26.1 no longer imports it, so the two have to move together. That is the only non-obvious part of this diff.

Also taking `grpcio` 1.78.1 → 1.83.1. Not a security alert, but the pinned release is yanked upstream and `uv` warns about it on every lock operation.

## What I did not change

`.github/dependabot.yml`. Its history reads as a deliberate position on update noise rather than an oversight — `ba838ed` limited pull requests to one a day, `76b33178` removed pip version updates, `09113e8` disabled pull requests entirely. Re-enabling would be reversing a maintainer decision, so it is yours to make. The consequence is that these will recur and need another manual `uv lock --upgrade-package` sweep; a periodic one may be preferable to the PR volume.

## Verification

- `uv sync --extra optional --extra property_prediction --dev` then `uv run pytest`: **352 passed**, no skips, matching the pre-upgrade count.
- `pre-commit run --all-files` clean apart from the node-based hooks, which cannot install node here; CI covers them.
- Lockfile only — no `pyproject.toml` change, so no effect on what users resolve.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6763ba2017f1`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
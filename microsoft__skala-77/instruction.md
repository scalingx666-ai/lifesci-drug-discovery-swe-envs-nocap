# Issue

**Title:** ci: pin GitHub Action refs to commit SHAs

## Description

## Why

Workflows referenced actions by **mutable tags** (e.g. `@v4`, `@release/v1`). Upstream maintainers, or an attacker who compromises their account, can force-push these tags to point at malicious code. Because our CI runs with repository secrets and write tokens (e.g. PyPI trusted publishing, GitHub Pages deploy), a poisoned action is a real supply chain risk.

## What

Pin every action `uses:` ref to the **immutable commit SHA** the tag currently points to, keeping the original tag as a trailing comment so the version stays readable and Dependabot can continue updating it.

```yaml
- uses: actions/checkout@34e114876b0b11c390a56381ad16ebd13914f8d5 # v4
```

While doing so, **unify the version of each action** across all workflows so the repository uses a single major version per action.

### Actions pinned
| Action | SHA | Tag |
|--------|-----|-----|
| actions/checkout | `34e1148` | v4 |
| actions/setup-python | `a309ff8` | v6 |
| actions/upload-artifact | `ea165f8` | v4 |
| actions/download-artifact | `634f93c` | v5 |
| actions/upload-pages-artifact | `56afc60` | v3 |
| actions/deploy-pages | `d6db901` | v4 |
| mamba-org/setup-micromamba | `4b9113a` | v1 |
| pypa/gh-action-pypi-publish | `cef2210` | release/v1 |

### Version unification
- `actions/setup-python`: was v5 (pypi.yml) / v6 (examples.yml) -> now **v6** everywhere.
- `actions/download-artifact`: was v4 (pypi.yml) / v5 (examples.yml) -> now **v5** everywhere.

## Drive-by fix

Removed an unused `# type: ignore[override]` on `gen_response` in `src/skala/pyscf/numint.py`. Under mypy strict mode, the comment is reported as unused in the lint environment (no cupy, so the `Array` TypeVar binds to `np.ndarray` and the override signature matches the base), which was failing the lint job.

## Impact

No workflow behavior changes; only the action references become tamper-proof and version-consistent.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `12e2b926accd`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
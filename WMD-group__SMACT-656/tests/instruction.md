# Issue

**Title:** ci: stop Dependabot auto-bumping torch/xgboost across a minor version

## Description

A routine grouped Dependabot bump (#634) moved `torch` from `nvidia-nccl-cu12` to `nvidia-nccl-cu13` while `xgboost` stayed on `cu12` — no declared version conflict, just two packages silently overwriting the same installed file (`nvidia/nccl/lib/libnccl.so.2`) on Linux, which broke torch's import. Fixed for the current pin in #654; this PR addresses how it got there in the first place.

There was no Python/uv ecosystem entry in `.github/dependabot.yml` at all — these `build(deps): bump the uv group...` PRs come from Dependabot's automated *security* updates (confirmed enabled repo-wide), which use unscoped default behaviour when no matching config exists.

Adds a `uv` ecosystem block:
- `open-pull-requests-limit: 0`, matching the existing `github-actions` block, so scheduled version-update PRs stay off — this is purely to let the `ignore` rules below apply.
- `ignore` rules excluding `torch` and `xgboost` from automatic minor/major bumps. Patch releases still flow through automatically; a version-generation bump now needs a human to run `uv lock --upgrade-package <name>` and check the resulting `nvidia-nccl-cuXX` pin still agrees between the two (per the constraint documented in `pyproject.toml`'s `property_prediction` extra).

This doesn't make the underlying collision impossible — nothing in pip/uv metadata expresses "these two packages write to the same file" — it just takes the routine, unreviewed path out of the loop for the two packages where it already bit us.

<!-- This is an auto-generated comment: release notes by coderabbit.ai -->

## Summary by CodeRabbit

- **Chores**
  - Automated dependency update monitoring has been configured for the project.
  - Patch-level updates for selected machine-learning dependencies can be applied automatically, while major and minor updates remain controlled to preserve compatibility.
  - Security update handling follows the same compatibility safeguards.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `97336357f0bf`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
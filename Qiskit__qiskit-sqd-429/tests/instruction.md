# Issue

**Title:** Update Fulqrum links for its move to the Qiskit org

## Description

Fulqrum moved from `qiskit-community` to `Qiskit`. This updates the four references in this repo.

The GitHub repo URLs 301-redirect, so those changes are cosmetic. The docs link was broken, but not by the move: it pointed at `qiskit-community.github.io/fulqrum/dev/`, and the docs have never been published under a `dev/` path. The `gh-pages` branch has a single deploy commit and a flat layout, so that link was broken from the start. It now points at https://qiskit.github.io/fulqrum/, which is both correct and consistent with how this repo links to every other `qiskit.github.io` site.

Files touched:

- `docs/guides/integrate_fulqrum.ipynb` — repo link and docs link
- `releasenotes/notes/0.14/fulqrum-8c940ab7c359ecdf.yaml` — repo link
- `.github/workflows/test_development_versions.yml` — `git clone` URL

<hr>

This pull request was drafted by Claude Opus 5 under my guidance.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `bf7714741be3`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
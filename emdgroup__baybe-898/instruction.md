# Issue

**Title:** Use `lychee` for docbuilding

## Description

This PR separates the linkcheck job from the actual doc building. It does so by creating a new dedicated job for it in the CI and re-organizing the code.

# External link checking
  - Replace Sphinx's `linkcheck` builder with lychee for external URL validation
  - Add a standalone lychee CI job that scans `baybe/`, `docs/`, `examples/`, and top-level markdown files
  - Configure exclusions in `lychee.toml` (migrated from `linkcheck_ignore` in `docs/conf.py`)
  - Remove the now-unused `linkcheck_ignore` from `docs/conf.py`

# Cross-reference checking
  - Switch the Sphinx build in check_links.py from linkcheck to dummy builder, which validates internal cross-references (:class:, :func:, :meth:, intersphinx) without rendering HTML
  - The dummy builder runs without -n/-W flags because it cannot fully resolve intersphinx references (e.g. ArrayLike), which would cause false positives; the html build with -n -W checks those

# Naming cleanup
  - Rename things related to `check_links` to `change_crossrefs`

# CI changes
  - Add lychee job to ci.yml, gating build-docs on both lint and lychee

# Misc
- The CI job shows all links that have been checked or excluded. Excluded links are the internal ones (as those are handled by `sphinx`). At the end of that job there is also a short summary (see screenshots)
- We would also be able use `lychee` for internal links but since the `sphinx html` build already does this, there is no further speed-up that we can gain here.
- Up-to-date version of the fork is available at https://avhopp.github.io/baybe_dev/latest/ (built after my latest commits answering to the first review of @Scienfitz )
- 
<img width="949" height="337" alt="image" src="https://github.com/user-attachments/assets/6170a96f-ed58-4ea2-8ba5-910e3916c28a" />
<img width="188" height="216" alt="image" src="https://github.com/user-attachments/assets/9941e0df-dbed-4776-a55a-11c78ddd9f09" />

---

<sub>Stack created with <a href="https://github.com/github/gh-stack">GitHub Stacks CLI</a> • <a href="https://gh.io/stacks-feedback">Give Feedback 💬</a></sub>

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5d727336f634`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
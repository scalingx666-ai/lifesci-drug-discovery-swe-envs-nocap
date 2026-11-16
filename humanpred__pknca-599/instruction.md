# Issue

**Title:** docs: refresh README, declare R (>= 4.1), and test that floor in CI

## Description

**README** (items 1–5 from the review):
- Development-version install uses `pak::pak()` rather than `remotes::install_github()`
- Adds a feature list — sparse sampling, units and preferred-unit conversion,
  imputation, CDISC output, bioequivalence. None were mentioned.
- Adds a **Documentation** section. The README linked to neither the pkgdown site,
  the user guide, nor any of the 20 vignettes.
- Drops `stringsAsFactors=FALSE` (the default since R 4.0)
- Points the best-practices badge at `bestpractices.dev` (the old host redirects
  twice, and the program is OpenSSF now, not CII)

**DESCRIPTION** gains `Depends: R (>= 4.1)`, which the package had never declared.

**CI** gains an `ubuntu-latest, r: '4.1'` job so the declared floor is exercised
rather than asserted.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `57bc31f57bfd`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
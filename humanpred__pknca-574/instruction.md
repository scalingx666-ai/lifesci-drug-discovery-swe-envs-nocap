# Issue

**Title:** Fix AUC to infinity subscript formatting in vignettes

## Description

Two malformed AUC-to-infinity subscripts in the vignettes:

- `v05-auc-calculation-with-PKNCA.Rmd` (AUC to Infinity section): `AUC~0-$\infty$,pred$` closed the pandoc subscript with a stray `$` instead of `~`, rendering a literal dollar sign with no subscripting. Now matches its `AUC~0-$\infty$,obs~` sibling.
- `v30-training-session.Rmd`: `AUC~0-\infty~` was missing the `$...$` inline-math delimiters, rendering a literal `\infty` in the subscript.

Verified both corrected lines through pandoc; they now produce proper `<sub>` markup with the ∞ symbol. All other `AUC~...~` occurrences across the vignettes were scanned and are well-formed.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f7cf919d7a80`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
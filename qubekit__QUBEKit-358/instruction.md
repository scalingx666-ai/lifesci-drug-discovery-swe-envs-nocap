# Issue

**Title:** Alpha and beta scaling with transfered polar H terms

## Description

## Description
This PR changes when the alpha and beta scaling are applied during the LJ derivation stage to allow them to be applied to polar Hs before being transferred to the parent atoms. So a scaled C6 term is derived for each atom then C6 prime on the parent is calculated from these terms.

This also fixes a bug in the polar h transfer code where the transfer was missed in protocol 4a as it assumed the presence of a polar H Rfree term under the normal key `X` which is not needed. Tests have been added to capture this failure in future and the reference values have been calculated by hand using the data in the `methanol.json` model in the data folder.

## Todos
Notable points that this PR has either accomplished or will accomplish.
  - [ ] TODO 1

## Questions
- [x] Expose as a flag when making the combined offxml? This will then remove the parameterization flag for the polar H as we don't want to take the gradient of the parameter which does not affect the parameters.
- [ ] This makes the XML combining code more complicated should we remove it as we can do everything via offxml now?

## Status
- [x] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c3444ece1686`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
# Issue

**Title:** Fix the atom indices of CXSMILES stereo groups

## Description

CXSMILES stereo groups (`a`, `&n`, `on`) were written through the inverse of the output order, so they land on the wrong atoms whenever the SMILES order differs from the atom order. `C[C@H](O)[C@H](N)C |&1:1,o1:3|` written as absolute CXSMILES gave `|o1:0,&1:3|`, two methyl carbons, instead of `|o1:1,&1:2|`.

The groups now use the output order, as the radicals have since 63147c15d5.

The test commit fails without the fix.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ddafddc16a8e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
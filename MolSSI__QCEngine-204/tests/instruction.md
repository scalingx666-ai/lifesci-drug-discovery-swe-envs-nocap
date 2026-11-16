# Issue

**Title:** NWCHEM:  added keyword dft to xc_functionals list.  If method == "dft"

## Description

<!-- Thank you for your contribution! -->

## Description
NWChem: added "dft" to list of exchange functionals.  If method == "dft" let exchange functional be handled by keywords.  Works with mixed functionals like "xc becke88 lyp".  This doesn't deal with cases like 'dft__xc': 'xc vwn_1_rpa 0.19 lyp 0.81 HFexch 0.20  slater 0.80 becke88 nonlocal 0.72'.

## Changelog description
NWChem: added "dft" to list of exchange functionals and let xc option be handled by keywords
## Status
<!-- Please `pip install .[lint]; make format` in the base folder. -->
- [X] Code base linted
- [X] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `fcd6f3ddc43a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
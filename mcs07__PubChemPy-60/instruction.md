# Issue

**Title:** Fix to_dict for substances lacking any compound record

## Description

Some substances data source in Pubchem does not provides compound value while other data source  provides. In this case, to_dataframe or to_dict funtion generate error no "compound"

ex: substance search with
"pcp.get_substances("65983-31-5", "name")"

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d94241fbc84d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
# Issue

**Title:** Only add volume and duration columns when they are given

## Description

PKNCAconc() filled a volume column with NA and a duration column with 0 on every dataset.  Both are only read by urine and fecal calculations, so a plasma analysis carried two columns that nothing used and that showed up whenever the object was printed (Fix #166).

The absent-input reporting introduced for volume now covers the collection duration too, so requesting an excretion rate (ermax, ertmax, ertlst) without a duration names those parameters instead of dividing by the defaulted zero and reporting infinite rates.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `7865450717f9`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
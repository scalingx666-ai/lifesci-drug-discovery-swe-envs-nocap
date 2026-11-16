# Issue

**Title:** swap carrier order in DoubleBondStereochemistry::create to satisfy bond alignment constraint

## Description

- fix carrier consistency in `DoubleBondStereochemistry::new`
- add tests for strict carrier swap behavior in `DoubleBondStereochemistry::new`
- change `DoubleBondStereochemistry::testMap_Map_Map` to reflect changes in `DoubleBondStereochemistry::create`

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f14d486d1368`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
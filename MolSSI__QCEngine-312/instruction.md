# Issue

**Title:** the regex parsing one

## Description

<!-- Thank you for your contribution! -->

## Description
<!-- Provide a brief description of the PR's purpose here. -->

## Changelog description
<!-- Provide a brief single sentence for the changelog. -->
- [x] parse available methods from CFOUR, GAMESS, NWChem
  *  mp3
  * mp4(sdq)
  * mp4
  * cisd
  * qcisd
  * qcisd(t)
  * ccd
  * lccd
  * lccsd
  * ccsd+t(ccsd)
  * a-ccsd(t)
  * ccsdt-1a, 1b, 2, 3
  * ccsdt
  * ccsdt(q)
  * ccsdtq
  * pbe
  * b3lyp
  * b3lyp5
- [x] includes alternate modules
- [x] often includes gradients and hessians
- [x] add reference values for the lot

*Review Note* These really are all tested but in qcdb, not here. There is an expanded test suite destined for here in qcng, but not the whole thing (that takes 90 min to run -n12).

## Status
<!-- Please `pip install .[lint]; make format` in the base folder. -->
- [x] Code base linted
- [x] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `8bef961f4343`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
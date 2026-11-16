# Issue

**Title:** cc2, cc3, bccd, cepa, dhdft, sdsc separation, zapt. format

## Description

<!-- Thank you for your contribution! -->

## Description
Develop stdsuite further for Psi4 and QCDB testing.

## Changelog description
<!-- Provide a brief single sentence for the changelog. -->
* Cfour
  * parsing for BCCD and BCCD(T)
* Gamess
  * CHANGE saving ROHF MP2 ZAPT quantities from MP2 to ZAPT qcvars
  * stop saving HF TOTAL ENERGY qcvar in DFT calcs, as it's not canonical HF energy
* NWChem
  * run b2plyp and parse and save dhdft qcvars correctly
  * collect cc2
* Refs and stdsuite
  * create different sections in ref storage for standard orbitals (SD) and semicanonical (SC) orbitals for CONV-AE-CONV and CONV-FC-CONV. SD's are small sections, and for AE, largely a copy from SC. This enables detangling CCSD and CCSD(T) reference duels that arise (1) because there are multiple legitimate formulations, esp. for FC ROHF and (2) while nearly all programs only produce SC CCSD(T), for CCSD programs produce only SC, only SD, or both, with varying defaults.
  * by default, SD sections are chosen for RHF and UHF and SC sections for ROHF. any downstream project using the stdsuite interface will need to add an extra argument.
  * add qcvars contracts for ZAPT2, CEPA(1), CEPA(3), ACPF, AQCC, BCCD, BCCD(T), CC2, and CC3
  * add qcvars contracts for DHDFT and check that it and plain DFT aren't setting HF and MP2 qcvars on non-canonical quantities
  * add references for the methods above mostly in CONV
  * in DF/CD, add refs for CCD and SVWN, WB97X, B2PLYP DFTs.

## Status
<!-- Please `pip install .[lint]; make format` in the base folder. -->
- [x] Code base linted
- [x] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `7f8c58a3b329`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
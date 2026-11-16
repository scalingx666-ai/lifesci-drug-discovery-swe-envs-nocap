# Issue

**Title:** Fresh PR for polariton-cq

## Description

Incorporates changes suggested by @loriab and @dgasmith and omits extra files accidentally incorporated in the SCF/ folder.

Description
This pull request provides reference implementations of hybrid ab initio / cavity quantum electrodynamics methods for computing mean-field ground- and excited-states of molecules strongly coupled to a single quantized photon.
What are your new additions? Please provide a brief list.
- New Features
   - [x] Restricted Hartree-Fock energy and orbitals for a molecule coupled to a single quantized photon provided in helper_CQED_RHF.py
   - [x] Configuration Interaction Singles energies and wavefunctions for a molecule coupled to a single quantized photon in helper_CS_CQED_CIS.py
   - [x] Ability to provide complex energy for the photon to account for dissipation / energy uncertainty in the photonic degree of freedom is provided in helper_CS_CQED_CIS.py
   - [x] Example calculations with tests are provided in CQED_RHF.py and CS_CQED_CIS.py
   - [x] Key equations and references provided in README.md
Any questions for the community?
- [ ] The CS_CQED_CIS has not been reported in the literature to my knowledge, so I don't know of peer-reviewed reference values, so the main independent test comes from the limit where the molecule is not coupled to a photon, where the method reduces to ordinary CIS which can be compared directly with Psi4 values - is that adequate?
Status
- [ ] Click when ready for review-and-merge

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ec36b7e062b5`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
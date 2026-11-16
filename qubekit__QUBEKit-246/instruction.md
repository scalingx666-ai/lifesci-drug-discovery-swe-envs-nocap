# Issue

**Title:** NB Param Storage

## Description

## Description
Store non bonded parameters in Ligand using new, specific containers. Better abstraction allows for full testing of v-sites, LJ, charge extraction etc.

## Todos
Notable points that this PR has either accomplished or will accomplish.
  - [X] Add new containers for non-bonded info.
  - [X] Update LJ, v-sites and charges to use these containers.
  - [X] Rework LJ polar Hs code. 
  - [X] Full fit tested for v-sites.
  - [X] Allowed for new LJ methods to be easily inserted into the new containers.
  - [ ] Symmetrisation needs to be reworked: overall but especially in LJ.
  - [ ] Need to extend testing for v-sites and LJ

## Questions
- [ ] Do we want to allow constraints to be tested, or just stick with "the best"?
- [ ] How do we want to handle symmetrisation? Once at the end? (Final params will change slightly depending on order.)

## Status
- [X] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6118e5218892`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
# Issue

**Title:** Kinase similarity demo mode

## Description

## Description
Make it easier to run the kinase similarity edition notebooks with a new set of kinases.

## Todos
- [x] Add `kissim` to environment
- [x] Add demo mode:
  - [x] Add a config file `pipeline_config.csv` next to `kinase_selection.csv` file with the following configurations
    - `DEMO`: `True` or `False` --- to run the notebooks exactly as displayed online; used in our CI)
    - `N_STRUCTURES_PER_KINASE` (has effect if `DEMO == True`) --- default is 3 (run KiSSim on 3 structures per kinase); if `None` use full dataset (this may take some time!)
    - `N_CORES` (has effect if `DEMO == True`) --- run KiSSim on user-specified number of cores (default is 1)
  - [x] T25/KiSSim and T26/IFP: Add `DEMO = True` at the beginning of the notebooks; if `False` do not freeze the set of KLIFS structures
  - [x] T25/KiSSim: Use `N_STRUCTURES_PER_KINASE` and `N_CORES`; add runtime warning for KiSSim
- [x] Generalize examples in T24/Seq and T27/Ligands so that notebook runs on kinases other than EGFR and MET (generalize variables and text also where needed)
- [x] Run notebooks on new dataset ([problem 1 in this paper](https://doi.org/10.1371/journal.pcbi.1009302)): RET, BRAF, SRC, S6K, MKNK1, TTK, ERK8, PDK, PAK3
  - [x] Get KLIFS names for these kinases
  - [x] Add this dataset to T23's quiz ("Rerun the notebooks on another kinase set, e.g. kinases XYZ)")
  - [x] Pipeline runs? Yes :)

## Questions
- [x] T27/Ligands: Make ChEMBL version more prominent? Added to "Aim of this talktorial section"

## Status
- [x] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `275c2741558b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
# Issue

**Title:** T019: Fix atom unit conversion

## Description

## Description
Fix problem as described in 

## Todos

- [x] Change `atom.unit` to `atom.units`
- [x] Fix Angström to nm conversion with `pint`(`mol_positions.to("nanometers")`)
- [x] Also: fix `openmm` warning - import `simtk.openmm` is now `openmm``
- [x] Also: Add MacOS/M1 conda note (`CONDA_SUBDIR=osx=64`)
- [x] Also: T019 runs for ages (>12 min) in CI!!!! Try using `mamba` instead of `conda` to install `openmmforcefield` within T019 > it seems to have worked, now only 2 min!!
- [x] Test only T019 (for now) - revert back to all notebooks in #308

## Status
- [x] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `87f4a451519b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
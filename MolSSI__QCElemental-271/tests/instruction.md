# Issue

**Title:** rel diff in array compare, symm in gamess str, more digits in Mol ctor

## Description

<!-- Thank you for your contribution! -->

## Description
<!-- Provide a brief description of the PR's purpose here. -->

## Changelog description
- [x] Molecule learned to create instances with geometry rounded to other than 8 decimal places through `Molecule(..., geometry_noise=<13>)` to optionally override `qcel.models.molecule.GEOMETRY_NOISE = 8`. This should be used sparingly, as it will make more molecules unique in the QCA database. But it is sometimes necessary for accurate finite difference steps and to preserve intrinsic symmetry upon geometry rotation. Previous route was to reset the qcel module variable for the duration of instance creation.
- [x] `Molecule.align` and `Molecule.scramble` learned to return a fuller copy of `self` than previously. Now has aligned `atom_labels`, `real`, and `mass_numbers` as well as incidentals like `Identifiers`. Fragmentation still not addressed.
- [x] `Molecule.to_string(dtype="gamess")` learned to write symmetry information to the prinaxis output if passed in through field `fix_symmetry`. This is provisional, as we'd like the field to be uniform across qcprogs.
- [x] `compare_values` on arrays corrected the RMS maximum o-e value displayed and added a relative value.

## Status
<!-- Please `pip install .[lint]; make format` in the base folder. -->
- [x] Code base linted
- [x] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6e101fb3f843`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
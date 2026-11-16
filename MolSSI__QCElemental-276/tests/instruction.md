# Issue

**Title:** nwchem ghosts, cancel list return for array properties

## Description

<!-- Thank you for your contribution! -->

## Description
<!-- Provide a brief description of the PR's purpose here. -->
Dev snapshot for qcdb testing. Ok to merge except for the dangerous line mentioned below. I may be able to find a way around it later.

## Changelog description
<!-- Provide a brief single sentence for the changelog. -->
- [x] `Molecule.align` learned ~`ghosts_distinguishable`~ `generic_ghosts` so that it can act on mols that have centers with content `Gh`, not `Gh(He)`.
- [x] `Molecule.to_string(..., dtype="nwchem")` learned to handle ghosts correctly. It also now prints the user label, which is used downstream for custom basis sets, but I'm not sure NWChem can process the full capability that Molecule labels allows. need to test.
- [x] `Molecule.to_string(..., dtype="gamess")` fixed an error, but actual ghosts are still NOT ready.
- [x] ~this bit https://github.com/MolSSI/QCElemental/compare/master...loriab:sept21qcdb?expand=1#diff-d903702553ee847b28a0f801ddd190627e98319531981cd4f29a3c0b7d27c57dR297 is dangerous and shouldn't be merged. it's sensible to not force array properties into lists forever, but QCFractal doesn't like it.~ @bennybp is willing to deal with this, so safe to merge

## Status
<!-- Please `pip install .[lint]; make format` in the base folder. -->
- [x] Code base linted
- [x] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `44fa853d5621`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
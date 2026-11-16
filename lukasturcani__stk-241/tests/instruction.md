# Issue

**Title:** Fix with_canonical_atom_ordering().

## Description

ConstructedMolecule.with_canonical_atom_ordering() now
also makes building blocks have canonical atom ordering.
This is necessary for databases which deposit constructed
molecules, and which require canonical ordering of all
molecules deposited. So when a ConstructedMolecule is
deposited, together with its building blocks, everyting is
canonical.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6b9173b0766f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
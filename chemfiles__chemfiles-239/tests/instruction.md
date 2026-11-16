# Issue

**Title:** Bug fixes

## Description

This PR has two bug fixes. 

- The first is rather minor and was the result of a typo in the PDB format code which resulted in improper linkage between peptide residues.

- The second is more complicated and involves the removal of atoms from a topology. Currently, when an atom is removed from a topology, the residues in that topology are not updated which leads to a misalignment of indicies above the index removed as well as a 'dangling' atom index. I've fixed this in two steps: the first is adding a method to the `Residue` class when removes atoms and updates the indicies above the removed index; the second is running this in a loop during the removal of an atom from a topology.

Note: I'm willing to update the other language bindings for residue atom removal as needed.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `add7ef672fae`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
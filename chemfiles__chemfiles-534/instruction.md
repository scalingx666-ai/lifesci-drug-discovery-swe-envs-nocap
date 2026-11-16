# Issue

**Title:** Bond O3' to P when linking nucleic acid residues in PDB files

## Description

When reading a PDB file, `link_standard_residue_bonds` links consecutive nucleotides with a bond from O3' of the previous residue to O3' of the current residue. It should be to .

The existing test for 2hkb.pdb didn't catch it because it only checks that the residues are linked. I added checks that O3' of residue 3 is bonded to P of residue 4 and not to its O3'.

I found this through Molly.jl, which uses the bonds from Chemfiles to match residue templates, so no DNA or RNA PDB file can be loaded there.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `51a17e85027c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
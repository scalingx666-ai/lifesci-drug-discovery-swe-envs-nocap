# Issue

**Title:** feat: adds method for generation and writing XYZ coordinates

## Description

I often directly write out the coordinates from a MolGraph object after modifying the Graph. For convenience I have added the two methods `to_xyz()` and `write_xyz(output_file)`. 

`to_xyz()` returns the molecule in XYZ format as string.
`write_xyz(output_file)` writes the string directly to a specified output file.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `7d8e22d1e96a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
# Issue

**Title:** Extended xyz

## Description

Fix #63 

This implement the extended XYZ format, using the XYZ comment line to store additional data. Most notably, this enable storing the unit cell for XYZ files!

Future extensions to this can include storing residue information, or other PDB style data in XYZ files.

The implementation is based on the libatoms documentation of the format, most notably supported by ASE: https://libatoms.github.io/QUIP/io.html#module-ase.io.extxyz. I was unfortunately unable to find an archived version of the original link in #63 (https://camtools.cam.ac.uk/wiki/site/5b59f819-0806-4a4d-0046-bcad6b9ac70f/Extendedxyz.html) to check for difference. It looks like it should be able to handle the version implemented by atomsk too (http://atomsk.univ-lille1.fr/doc/en/format_xyz.html)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `47e4319a9dec`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
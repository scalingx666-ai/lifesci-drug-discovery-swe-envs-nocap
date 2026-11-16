# Issue

**Title:** Base.multimedia.display(mol)

## Description

Implements `Base.Multimedia.display` for `GraphMol` objects, so that they can easily be displayed in Pluto notebooks.

Addresses #64 (closes?)

![image](https://user-images.githubusercontent.com/16201240/191818059-299afb98-7415-4c53-8b68-5db59a835f38.png)

Implementation sets a default 250 px * 250 px size for the SVG and allows positional input of custom render dimensions.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `00c880e6b11b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
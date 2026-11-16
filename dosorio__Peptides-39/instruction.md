# Issue

**Title:** Integration of labelling at C- and N-terminus

## Description

Hi!
Sorry for the second PR. I forgot to update the `Readme.md` to include the new functions. Also, I integrated a new feature in the `massShift` function: you can now also add labels at the N-terminus or C-terminus, independent of the amino acid sequence. 
Also, the input in `aaShift` is now tested and a specific error message is given, if the input cannot be matched to a standard amino acid.
Greetings, Florian

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `72646e52c7b1`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
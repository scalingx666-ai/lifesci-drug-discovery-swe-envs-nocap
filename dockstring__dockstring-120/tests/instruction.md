# Issue

**Title:** Add openbabel version checking command to target.dock

## Description

I just accidentally tried docking in a conda env without open babel and the error I got was that "protonation failed". While this is technically true because protonation requires openbabel, I think it would be better to output a more specific error message if openbabel is not installed.

My solution: when calling `target.dock`, call `obabel -V` and check that this command succeeds and that the version is right. This seems like a simple solution, although currently the openbabel version is hardcoded which isn't ideal. Thoughts @gncs  @mgarort ?

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e1790c12575f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
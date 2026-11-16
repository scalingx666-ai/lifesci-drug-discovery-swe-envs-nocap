# Issue

**Title:** Add the option to locate a IChemObject builder using reflection. Enfo…

## Description

…rce the RDfile reader has one.

Different Java version's didn't like a piece of code the the RDfile reader constructor - I spotted it when I wrote the sample code for the release and accidentally committed it here: 

I have added the option for the IChemObjectBuilder to look one up via reflection, @egonw  and I have talked about this previously.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f351dd020de0`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
# Issue

**Title:** RMSD with multicore and timeout functionality

## Description

As we discussed in #105: here is my first shot at implementation of RMSD functions with multicore and timeout functionalities.

For now, I kept the `rmsd_timeout` function public, however we could also just make it private. This function supports a molref with multiple mols, something that the multicore function doesn't support directly (everything is done pairwise here). Although I guess there is an easy workaround for the user? 
Maybe it's even better to implement this ourselves: if only one mol is supplied as the ref mol, extend the list to match the length of the mol list? (like this `[refmol]*len(mols)`). This would also give each molecule a seperate timeout. Having the possibility of a mollist in the `rmsd_timeout` function also made me return the raw result of rmsdwrapper (a list) instead of the value (because otherwise only one value would be returned). So if we make it private, it could clean up things and also emulate the regular rmsdwrapper functionality better! (I just came up with this while writing this description, if you like it I will implement it tomorrow!)

I also still need to add tests. I guess we could add a test for a timeout, a test for matching mols and molrefs list, ... But multicore might be harder to test?

Any feedback welcome as always! 

Note: I intentionally kept all the new funtions and imports together at the bottom so it's more clear to see what's added. This makes Flake8 doesn't pass. MyPy also doesn't pass yet, but I'll get to fixing that tomorrow as well!

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `8ce0edea593d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
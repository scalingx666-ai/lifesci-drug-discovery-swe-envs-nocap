# Issue

**Title:** Fixed DockStream issue: Outputting 0 Docking score values for all mol…

## Description

**Description:**
I was trying to implement the DockStream RL workflow from one of the notebooks on my HPC Linux system with the Openeye Omega & Hybrid programs but kept getting 0.000 docking scores for all molecules which seemed a bit odd (**this was before I read that you don't support DockStream anymore**). 

Anyway, I dove deep into the DockStream-Reinvent source code (nicely written btw) to find the fault as I tested and Dockstream with OE programs worked fine executed outside of Reinvent. 

There is a tiny issue of how the smiles values are provided within the subprocess command inside comp_dockstream.py that Reinvent seems to not like very much. Works fine after the fix though!

I can also write a workflow notebook for the OE-DockStream combo if it would be useful to anyone, shame about DockStream though I just started to like it! Will start studying up on maize when I get a chance

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `4bd6152895ac`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
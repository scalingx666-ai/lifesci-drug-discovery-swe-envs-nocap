# Issue

**Title:** Fix for AMBER uncapped terminals crashing tleap

## Description

So if you try to build a protein in AMBER which doesn't have caps you will run into the issue that the caps have different atom names for the hydrogens.
For example if you have a terminal HID residue with a H atom, once tleap tried to build it it will rename it to NHID and crash because there is no H atom in NHID, just H[123].
Removing all hydrogens from all terminals was the easiest solution. According to @cuzzo87 it should not matter anyway as the H positions in terminals are equivalent.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `eda184638f27`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
# Issue

**Title:** Aligns DOS to Fermi level

## Description

This fixes an alignment issue with DOSes that caused them to not line up with Bandstructures when aligning to the Fermi-level

 - Added zero_to_efermi to SDOSPlotter.dos_plot_data

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2a12ddb12ad3`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
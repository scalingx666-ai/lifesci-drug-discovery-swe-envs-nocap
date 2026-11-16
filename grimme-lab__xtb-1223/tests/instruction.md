# Issue

**Title:** Fix NaN Fermi-level

## Description

Fix for the NaN value of the Fermi-level if there are no electrons in either alpha or beta (or both) channels. Now, the Fermi-level is set to the lowest available eigenvalue. This leads to a consistent Fermi-level for radicals, where the alpha and beta levels are averaged. Additionally, I combined all checks for the applicability of Fermi smearing (i.e. whether the species has virtual orbitals) in the same place. I checked that FOD remains unchanged. This should address #1169. 

Closely related to this, I skipped the MO localization with the `--lmo` flag if there is no electron present. This leaves the output unchanged (i.e. the analysis and output files remain the same) but avoids MKL issues during the matrix multiplication if the number of occupied orbitals is zero. I added a warning if the localization is applied without occupied orbitals. This should fix #1033.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `7d4041b48c06`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
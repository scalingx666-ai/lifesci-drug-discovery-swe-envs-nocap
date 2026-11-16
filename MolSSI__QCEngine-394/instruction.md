# Issue

**Title:** fix qcore and adcc CI

## Description

<!-- Thank you for your contribution! -->

## Description
<!-- Provide a brief description of the PR's purpose here. -->
* according to https://software.entos.ai/qcore/tutorial/ , entos needs a tbb constraint. that fixes the CI error that was showing up at license check time
* @maxscheurer, I think what was happening with the h5 error in adcc CI (e.g., https://github.com/MolSSI/QCEngine/actions/runs/3847917831/jobs/6555003472) was that psi needs hdf5 1.10, and with c-f higher in channel priority, it was having to grab old h5py 3.3 since c-f switched to 1.12 earlier. Now it's getting 1.10-based hdf5 packages from defaults and adcc itself from c-f instead of adcc channel. Presently adcc 0.15.14 and psi4 1.7.

## Changelog description
<!-- Provide a brief single sentence for the changelog. -->

## Status
<!-- Please `pip install .[lint]; make format` in the base folder. -->
- [x] Code base linted
- [x] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c68b54709b7a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
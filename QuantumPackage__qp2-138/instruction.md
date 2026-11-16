# Issue

**Title:** Fix space in size for EZFIO.cfg

## Description

People do strange things (By people I mean @anbenali), they put space in EZFIO.cfg size.
```
[qmc_phase]
type: double precision
doc: phase for reconstruction of supercell from k-points
interface: ezfio
size: (2, nuclei.kpt_num, nuclei.kpt_num)
```
Everybody knows that you should not do that..! But anyways, my goal is to make people happy so I fixed the EZFIO.cfg parser to support that.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e2e500dad8e4`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
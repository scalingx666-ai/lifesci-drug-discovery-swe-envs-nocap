# Issue

**Title:** Prevent concurrent CPCM-X testing

## Description

Avoids concurrent CPCM-X testing, which can delete the .cosmo files between runs.

Addresses test runs such as [this](https://github.com/grimme-lab/xtb/actions/runs/42000652833/job/127154706058?pr=1508)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b188560cc531`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
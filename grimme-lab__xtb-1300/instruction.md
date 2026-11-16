# Issue

**Title:** Avoid meson 1.8.1

## Description

Meson 1.8.1 is still not stable for configuring xtb builds. See errors here:
https://github.com/grimme-lab/xtb/actions/runs/15366340755?pr=1298

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `fe1c8ce9d25b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
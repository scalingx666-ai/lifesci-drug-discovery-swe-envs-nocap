# Issue

**Title:** Remove method logging decorators; moved ONETEP param extraction to fi…

## Description

…le handers; improved LJ calcs; added charge checking when using v-sites; updated v-sites to better handle multiple sites per molecule; improved symmetric v-site calc; other small fixes.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1465de0a9e60`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
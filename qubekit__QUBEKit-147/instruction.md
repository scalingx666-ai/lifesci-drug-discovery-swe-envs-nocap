# Issue

**Title:** Integrated v-sites into run.py (charges stage); amended xyz reader to…

## Description

… handle xyz's not from ONETEP; fixed extraction of v-sites from xyz in lennard_jones.py; added execution description to virtual_sites.py; moved logic from VirtualSites init to its own method.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `47e229184202`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
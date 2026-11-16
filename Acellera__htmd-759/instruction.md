# Issue

**Title:** Modified opm method

## Description

url for retrieving pdb has changed in opm webserver.
Using `4eiy` as example it has just modifeid from `http://opm.phar.umich.edu/pdb/4eiy.pdb` to `https://storage.googleapis.com/opm-assets/pdb/4eiy.pdb`

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `8f5c43282236`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
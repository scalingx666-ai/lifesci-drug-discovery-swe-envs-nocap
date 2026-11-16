# Issue

**Title:** fix miRge DM and change cutoff param default

## Description

FOR CONTRIBUTOR:
* [ ] I have read the [CONTRIBUTING.md](https://github.com/galaxyproject/tools-iuc/blob/master/CONTRIBUTING.md) document and this tool is appropriate for the tools-iuc repo.
* [ ] License permits unrestricted use (educational + commercial)
* [ ] This PR adds a new tool or tool collection
* [x] This PR updates an existing tool or tool collection
* [x] This PR does something else (explain below)

Fix the miRge DM that was only downloading the hamster library. Also change the default value of param as discussed here:

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `10636efa2c06`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
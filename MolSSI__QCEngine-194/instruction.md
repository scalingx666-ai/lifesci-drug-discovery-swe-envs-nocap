# Issue

**Title:** dftd3 variant error

## Description

## Description
I'm not able to reproduce #186 easily. And it's true that that error is always user input these days. The variant not available was true in 2016, but those executables should have aged out. I think the `get_version` may even filter them away. So on the basis of the aforementioned hunch, I'm just reclassifying. 

## Questions
- [ ] Should I have changed the error type or just the message?
- [ ] `make format` changed _a lot_, including breaking black on nwchem/harvester. I've seen those changes in other PRs so didn't include them here.

## Status
- [ ] Changelog updated
- [ ] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `16194de6b666`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
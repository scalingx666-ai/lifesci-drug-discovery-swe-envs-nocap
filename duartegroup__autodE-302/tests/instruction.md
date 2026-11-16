# Issue

**Title:** Faster IDPP

## Description

Remove parallelisation from IDPP. The overhead from creating new processes is larger than any gains from parallelisation.

Test for diels-alder with 200 IDPP images
 - MacOS - with parallelisation = 4.621 s, without parallelisation = 2.403 s
 - Windows - with parallelisation = 10.26 s, without parallelisation = 2.331 s

***

## Checklist

* [ ] The changes include an associated explanation of how/why
* [ ] Test pass
* [ ] Documentation has been updated
* [ ] Changelog has been updated

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `db7b03d335b3`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
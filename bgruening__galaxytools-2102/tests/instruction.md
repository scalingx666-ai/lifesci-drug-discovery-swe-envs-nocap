# Issue

**Title:** Update 3dtrees_potree to 1.3.0

## Description

<!-- claude-projects-attribution: {"github_login":"kgerb"} -->
_Requested by **Kilian**_

FOR CONTRIBUTOR:
* [X] I have read the [CONTRIBUTING.md](https://github.com/galaxyproject/tools-iuc/blob/master/CONTRIBUTING.md) document and this tool is appropriate for the tools-iuc repo.
* [X] License permits unrestricted use (educational + commercial)
* [ ] This PR adds a new tool or tool collection
* [X] This PR updates an existing tool or tool collection
* [ ] This PR does something else (explain below)

Updates the 3Dtrees Potree Converter to [v1.3.0](https://github.com/3dTrees-earth/3dtrees_potree/releases/tag/v1.3.0). The tool now converts point clouds above 2^32 points and very dense volumes, which crashed or stalled in 1.2.1, and runs much faster on large inputs. The form is unchanged.

Adds one test with two input files, which crashed in 1.2.1. `planemo test` passes all 3 tests locally against the released image.

After merge: install 1.3.0 on Galaxy EU, then point the 3Dtrees production workflows at the new version.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `db60013c3dd3`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
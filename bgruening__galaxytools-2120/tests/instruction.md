# Issue

**Title:** Update 3Dtrees: ForestMamba 1.0.2

## Description

<!-- claude-projects-attribution: {"github_login":"kgerb"} -->
_Requested by **Kilian**_

FOR CONTRIBUTOR:
* [X] I have read the [CONTRIBUTING.md](https://github.com/galaxyproject/tools-iuc/blob/master/CONTRIBUTING.md) document and this tool is appropriate for the tools-iuc repo.
* [X] License permits unrestricted use (educational + commercial)
* [ ] This PR adds a new tool or tool collection
* [X] This PR updates an existing tool or tool collection
* [ ] This PR does something else (explain below)

Updates 3Dtrees ForestMamba from 1.0.1 to [1.0.2](https://github.com/3dTrees-earth/3Dtrees_ForestMamba/releases/tag/v1.0.2) (image `ghcr.io/3dtrees-earth/3dtrees_forestmamba:1.0.2`, released). The form and the results are unchanged.

- Fits a 16 GB GPU such as a Tesla T4: peak 8–9 GB of GPU memory on the densest windows of a 158 M-point tile, where 1.0.1 runs out of memory.
- About a third less host memory (whole-run peak 28.0 → 19.4 GB on that tile).
- Tiles with a single point no longer fail.

The test still expects the no-GPU failure on GitHub CI and checks that the bluepoint defaults reach the tool.

Related: TPV rule allowing the T4 for 1.0.2 and later, usegalaxy-eu/infrastructure-playbook#2523.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `7682360a0217`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
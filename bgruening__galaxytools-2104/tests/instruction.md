# Issue

**Title:** Update 3Dtrees: ForestMamba 1.0.1

## Description

<!-- claude-projects-attribution: {"github_login":"kgerb"} -->
_Requested by **Kilian**_

FOR CONTRIBUTOR:
* [X] I have read the [CONTRIBUTING.md](https://github.com/galaxyproject/tools-iuc/blob/master/CONTRIBUTING.md) document and this tool is appropriate for the tools-iuc repo.
* [X] License permits unrestricted use (educational + commercial)
* [ ] This PR adds a new tool or tool collection
* [X] This PR updates an existing tool or tool collection
* [ ] This PR does something else (explain below)

Updates 3Dtrees ForestMamba from 1.0.0 to 1.0.1.

- Loads the correct model checkpoint. The 1.0.0 image loaded a mismatched checkpoint, so part of the model ran with random weights.
- Runs about 40 % faster and leaves small fragments from the second bluepoint pass unassigned.
- Bluepoint iterations now default to `2` (was `0`), so dense stands get the second pass.
- New parameter `--bluepoint-min-tree-points` (default `300`).

Draft until the `ghcr.io/3dtrees-earth/3dtrees_forestmamba:1.0.1` image is re-released with these changes. The test still expects the no-GPU failure on GitHub CI.

After merge: install 1.0.1 on Galaxy EU, then point the 3Dtrees production workflows at it.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `39ce1f0f30d9`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
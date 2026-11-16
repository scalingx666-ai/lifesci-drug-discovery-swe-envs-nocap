# Issue

**Title:** Update 3dtrees_sidecar to 0.1.1

## Description

<!-- claude-projects-attribution: {"github_login":"kgerb"} -->
_Requested by **Kilian** · [project thread](https://claude.ai/code/project/chan_01DMg1jiAvtyYXCxTqevHXvC?thread=cmsg_01DMg1jiAvtyYXCxTqevHXvC4AvmmRZTV2671VFsxFJFvT)_

FOR CONTRIBUTOR:
* [X] I have read the [CONTRIBUTING.md](https://github.com/galaxyproject/tools-iuc/blob/master/CONTRIBUTING.md) document and this tool is appropriate for the tools-iuc repo.
* [X] License permits unrestricted use (educational + commercial)
* [ ] This PR adds a new tool or tool collection
* [X] This PR updates an existing tool or tool collection
* [ ] This PR does something else (explain below)

Updates 3Dtrees: Sidecar to [v0.1.1](https://github.com/3dTrees-earth/3dtrees_sidecar/releases/tag/v0.1.1).

- **Rounding fix:** assemble and check no longer round float attributes that carry a scale, so point clouds with such attributes now pass the check.
- **Clearer rejections:** export refuses scaled columns with a clear message, and a LAS 1.0 input fails with a one-line message instead of a traceback.
- **Form:** unchanged.

`test-data/sat.parquet` is regenerated because the sidecar stores the tool version in its metadata; the data is identical. All wrapper test outputs match the released image byte for byte.

After merge: install 0.1.1 on Galaxy EU, then point the 3Dtrees production workflows at the new version.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `cf3d3559b610`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
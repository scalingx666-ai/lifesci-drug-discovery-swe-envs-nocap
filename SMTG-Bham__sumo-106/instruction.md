# Issue

**Title:** Pass bandplot range to CASTEP DOS

## Description

Fix a bug reported by @jryates; when adding a DOS to a CASTEP band structure, the --ymin and --ymax values were not being passed to the DOS plotter. The results are not pretty:

![bad-band](https://user-images.githubusercontent.com/2511383/87779341-8d1bab00-c824-11ea-9f35-ed922a25b8ea.png)

Passing the options seems to clean this up:
![band](https://user-images.githubusercontent.com/2511383/87779562-e1268f80-c824-11ea-85f7-f3503ad12c76.png)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `eb964951b1e4`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
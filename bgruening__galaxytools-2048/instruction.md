# Issue

**Title:** firm up tool bot across fork checks

## Description

initial forks check were a bit naive, but i dont have prs from forks to check against very well- so youre a bit a guinea pig currently, sry. this should also get within repo feedback flows working again, thats a related issue actually. first thing it does is check if its in a fork, and thats not working right yet apparently.. :crossed_fingers: this restores that

i mean to sort out a safe path for fork pr review flow soon, but am becoming skeptical i can get feedback to work in a way i trust for fork prs.

FOR CONTRIBUTOR:
* [x] I have read the [CONTRIBUTING.md](https://github.com/galaxyproject/tools-iuc/blob/master/CONTRIBUTING.md) document and this tool is appropriate for the tools-iuc repo.
* [x] License permits unrestricted use (educational + commercial)
* [ ] This PR adds a new tool or tool collection
* [ ] This PR updates an existing tool or tool collection
* [x] This PR does something else (explain below)

There are two labels that allow to ignore specific (false positive) tool linter errors:

* `skip-version-check`: Use it if only a subset of the tools has been updated in a suite.
* `skip-url-check`: Use it if github CI sees 403 errors, but the URLs work.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `155bd58df953`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
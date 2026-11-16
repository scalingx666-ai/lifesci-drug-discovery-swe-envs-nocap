# Issue

**Title:** Some Turbomole fixes

## Description

<!-- Thank you for your contribution! -->

## Description
<!-- Provide a brief description of the PR's purpose here. -->
This PR incorporates some fixes/additions for the Turbomole runner:
- Pass SCF convergence and SCF max. iterations to `define`
- Correctly enable OMP
- Pass `environment` to `execute`

@loriab I'm actually @maxscheurer but from my corporate GH account 😄 

## Questions
- [x] Is the new test okay using `xfail`?
- [ ] How should one allow a user-specified scratch directory? Is `TaskConfig` -> `execute` the correct route?
- [ ] I changed the (unusual?) `jobs_per_node` default from `2` to `1`, is that okay, or was there a reason for it being set to `2` specifically?
- [ ] `make format` reformats almost all files...

## Changelog description
<!-- Provide a brief single sentence for the changelog. -->

## Status
<!-- Please `pip install .[lint]; make format` in the base folder. -->
- [ ] Code base linted
- [ ] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `bededd8b0e30`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
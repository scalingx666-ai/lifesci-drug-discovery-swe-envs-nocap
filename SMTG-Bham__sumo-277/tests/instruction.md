# Issue

**Title:** Update release action

## Description

The release action was on an older python. I also updated it to use more modern/recommended PyPI authentication (i.e. the action is whitelisted from PyPI side and doesn't use a password from `secrets`.)

That succeeded in building and pushing to PyPI, but failed to create a Github release 🤦 

https://github.com/SMTG-Bham/sumo/actions/runs/24199863780/job/70640200234

I think I need to set "write-all" permission instead of "write": https://stackoverflow.com/questions/70435286/resource-not-accessible-by-integration-on-github-post-repos-owner-repo-ac

Given that the release is on PyPI the correct cleanup option is probably to create a manual release on Github now.

I'll also update the permission to "write-all" here, which _hopefully_ will fix it next time.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `868353ce553d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
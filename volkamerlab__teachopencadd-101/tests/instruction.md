# Issue

**Title:** Reenable Binder

## Description

I wanted to get rid of some environment.yml duplication but didn't remember that Binder depended on that. I've fixed that problem now, mentioned in #100 

The Binder env is now under `.binder/environment.yml`, which is a symlink to `devtools/test_env.yml`. Notice that `test_env.yml` is not under `conda-envs` anymore so we can use the same relative path for TeachOpenCADD (`../` instead of `../../`).

@dominiquesydow, you ok with these changes?

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1590ccb5ffa0`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
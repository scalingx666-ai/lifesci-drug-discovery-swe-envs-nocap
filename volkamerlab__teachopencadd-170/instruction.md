# Issue

**Title:** Changes after conda-forge package release

## Description

## Description
Update the repo after the package has been released on conda-forge.
This PR will be in progress parallel to the conda-forge submission.

## Todos
- [x] Submit package to conda-forge: 
- [x] Dependencies?
  - [x] Remove [`autodocktools` pip install](https://github.com/volkamerlab/teachopencadd/blob/c3a6308a706f0c842171e905e5685295e220e763/devtools/test_env.yml#L63) - notebooks still running? yes
  - [x] No `openff` under Windows, is that a problem? No, `openff` is not part of our `test_env.yml` file, it is installed [manually in T019](https://projects.volkamerlab.org/teachopencadd/talktorials/T019_md_simulation.html#Adjust-environment-for-local-installations-running-on-Linux-or-MacOS)
- [x] Remove [this](https://github.com/volkamerlab/teachopencadd/blob/master/devtools/conda-recipe/meta.yaml) recipe (now on cf)
- [x] Update [test env](https://github.com/volkamerlab/teachopencadd/blob/master/devtools/test_env.yml)
- [x] Remove [user env](https://github.com/volkamerlab/teachopencadd/blob/master/devtools/other-conda-envs/users_env.yml) (replaced by using the conda package)
- [x] Update the [documentation](https://projects.volkamerlab.org/teachopencadd/installing.html) (use package installation)
- [x] Remove [this bit](https://github.com/volkamerlab/teachopencadd/blob/c3a6308a706f0c842171e905e5685295e220e763/.github/workflows/ci.yml#L109-L146) from the CI (once package on cf)

## Questions
None.

## Status
- [x] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `7c60814c3bb9`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
# Issue

**Title:** Add `numpy`+`jsonschema` to env + drop Python 3.6 in CI (use 3.7 instead)

## Description

## Description
See issue: 

## Todos
- [x] Fix env (workaround): `numpy` version conflicts with `mdanalysis`: Add `numpy` to `test_env.yml`
- [x] Fix env (workaround): `jsonschema` version shipped with `bravado` (<4.0.0) comes without a necessary module, thus manually install `jsonschema` <4.0.0 here *until this is fixed in bravado/swagger_spec_validator or else - REVISIT THIS* Opened issue as a reminder: 
- [x] Config CI for Python 3.7 instead of 3.6
  - Python 3.6 support may become more and more complicated with that many packages we are using
  - Examples
    - 
    - https://deeptalk.lambdalabs.com/t/cant-build-keras-model-after-tensorflow-update-from-2-2-to-2-3/1799
    - https://bugs.gentoo.org/806541 
- [x] Add comment  to envs "Explicitly add numpy because: "
- [x] Streamline all envs: test and users envs
- [x] Check if CI passes

## Questions
None

## Status
- [x] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `268484793c5c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
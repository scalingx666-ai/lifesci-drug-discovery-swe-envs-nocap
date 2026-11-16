# Issue

**Title:** Detect ifx (intel-llvm) when determining compiler settings

## Description

* Use `fc_id` throughout meson.build, rather than repeatedly calling `fc.get_id()`. 
* Wherever we previously branched for `"intel"` (ifort compiler), also branch for `"intel-llvm"` (ifx compiler).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ec4f3887e143`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
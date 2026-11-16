# Issue

**Title:** build: bump tree.hh to 3.18

## Description

I’m not sure if this  because I *can* build openbabel with GCC 16.2.1 on EndeavourOS.
<!-- <https://gitlab.archlinux.org/archlinux/packaging/packages/openbabel/-/blob/e4ebc88a3015914fe60d8e7f00e4b8ad6b974d05/PKGBUILD> -->

But tree.hh is outdated anyway.
https://github.com/openbabel/openbabel/blob/1afe81019b781c857eecb86251e106e2f31da928/include/openbabel/tree/tree.hh#L10-L15
<http://www.aei.mpg.de/~peekas/tree/> seems gone; [GH kpeeters/tree.hh tags only 3.16 and 3.18](https://github.com/kpeeters/tree.hh/releases).

## Summary by Sourcery

Replace the outdated bundled tree.hh implementation with the maintained tree.hh 3.18 dependency and ensure CI and builds initialize it correctly.

Enhancements:
- Update the tree.hh dependency to the current version through an external submodule and use it for conformer searching.
- Add CMake validation and include configuration to require the tree.hh submodule when Eigen-based builds are enabled.

CI:
- Ensure GitHub Actions workflows check out recursive submodules for bindings, CMake, and wheel builds.

Chores:
- Remove the bundled legacy tree.hh and tree_util.hh copies in favor of the external dependency.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1afe81019b78`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
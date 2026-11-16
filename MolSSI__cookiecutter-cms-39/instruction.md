# Issue

**Title:** Update many things, mostly travis

## Description

* Change Cookiecutter testing scheme to test all python versions and OS combinations
* Update Travis script to correctly handle their OSX platform missing `pip` after xcode 7.3.
    * After much trial and error, using `brew`->`pyenv` to be done with it. 
    * See notes in the bash source file in the new `cihelpers` folder. 
* Use `--no-deps` when when using conda for packages to prevent pip from installing them
    * Cannot use `python setup.py develop --no-deps` because then conda does not recognize the package installed correctly and cannot execute its `test` block since it won't find the package.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c6556a251558`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
# Issue

**Title:** Add testing with Intel compilers

## Description

- builds crest with Intel oneAPI classic compilers using meson
- installs xtb from selected release in testing environment
- runs example 0 to check for basic functionality
- also comments out `crest_combi` script installation

Here is also a test run including all examples to check for timings in the runner environment:
https://github.com/awvwgk/crest/runs/1806684235?check_suite_focus=true

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `348d53e90fff`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
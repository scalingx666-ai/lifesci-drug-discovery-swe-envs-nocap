# Issue

**Title:** Add GPU testing workflows and add gpu tox configuration

## Description

This PR adds a dedicated Tox environment for GPU-related tests and one manual workflow as well as additional steps to regular and CI for installing and starting those tests. At the moment, they are only executed if triggered manually and if core tests have passed. Support for other triggers is WIP. Additionally, I've changed the Benchmark installation to UV and added terminal outputs of standard resource commands for CPU, RAM and so on.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `abe80d39633e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
# Issue

**Title:** Add `atomate2` and `jobflow` `MLFF MD` local workflow support

## Description

- Restrict `mp-api==0.40.0` as it updates frequently and has been unstable
- Use local file system as default to transfer structure information as `pymatgen` `Structure` is too verbose and contains too much repetitive information. This reduces the likelihood of text generation mistake and increases overall speed. The original `text` mode is still there
- Support `jobflow` `run_locally` and add flow to `FireWorks` launchpad. The default `run_mode` is set to `local`

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d9369682c583`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
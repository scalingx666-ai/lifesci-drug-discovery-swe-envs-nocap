# Issue

**Title:** Pin onnxruntime version due to lacking python 3.10 support

## Description

Release `1.24.1` of `onnxruntime` dropped support for Python 3.10, see https://github.com/microsoft/onnxruntime/releases/tag/v1.24.1. Unfortunately, they did not properly update their metadata, which causes issues when trying to install the package as `uv` *thinks* that python 3.10 is still supported for several versions that actually do not support this anymore. The metadata was only fixed recently in https://github.com/microsoft/onnxruntime/releases/tag/v1.24.4 (see ).

Although this does not cause issues when *updating* the lock file, it creates issues when it has to be fully regenerated which e.g. happens in #771 .

It is thus necessary to pin the used version of `onnxruntime` for python 3.10.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b9cd5c4087bf`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
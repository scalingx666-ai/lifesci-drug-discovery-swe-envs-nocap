# Issue

**Title:** Bug: Fix Serializaion of single number tensors

## Description

Currently tensors with a single value do not survive the roundtrip of json-serialization.
Fix: save data as numpy array, and reconstruct from there.

ToDos:
- [x] Implement unit-test for original bug
- [x] implement serialization of numpy arrays and dypes
- [x] fix bug with saving tensors where data is captured as serialized numpy array
- [x] Add Tests for numpy logic

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `68c7ec7c90cf`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
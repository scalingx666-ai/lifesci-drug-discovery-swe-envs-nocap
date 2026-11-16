# Issue

**Title:** Add plain msgpack serialization

## Description

<!-- Thank you for your contribution! -->

## Description
<!-- Provide a brief description of the PR's purpose here. -->

Adds ability to serialize to plain msgpack format.

The current `msgpack-ext` encoding serializes numpy arrays as numpy arrays, which is not portable (that is, deserializing would require python and qcelemental). This adds a plain `msgpack` encoding that converts numpy arrays to lists, as is done with the existing `json` encoding.

## Changelog description
<!-- Provide a brief single sentence for the changelog. -->
Adds plain msgpack serialization

## Status
<!-- Please `pip install .[lint]; make format` in the base folder. -->
- [X] Code base linted
- [X] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5e413e62cddf`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
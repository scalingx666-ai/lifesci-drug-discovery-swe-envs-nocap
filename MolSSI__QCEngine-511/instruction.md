# Issue

**Title:** Add put xml line to molpro input builder.

## Description

<!-- Thank you for your contribution! -->

## Description
<!-- Provide a brief description of the PR's purpose here. -->
After a certain version, MolPro reduced the amount of output in their XML dump. The way to get the old style back is to add a line containing `{put,xml}` at the point where you want it to put its information. It is currently set to put it at the end. This will hopefully capture the last energy calculation and optional gradients.

## Changelog description
<!-- Provide a brief single sentence for the changelog. -->
Updated MolPro XML output to take the new default dump level into consideration.

## Status
<!-- Please `pip install .[lint]; make format` in the base folder. -->
- [x] Code base linted
- [x] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `74684488deca`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
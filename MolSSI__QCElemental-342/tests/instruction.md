# Issue

**Title:** need graphviz

## Description

<!-- Thank you for your contribution! -->

## Description
<!-- Provide a brief description of the PR's purpose here. -->
- [x] I strongly suspect this'll fix #333 which wasn't working b/c `dot` not present b/c it can't be installed by pypi. (Can be installed thru conda.) Fortunately there's a GHA action to the rescue.
- [x] Missing class docstrings were generating `ERROR: Content block expected for the "raw" directive; none found.`
- [x] the unescaped `qc_` were being interpreted as sphinx links
- [x] I don't think there's harm in importing `nglview` with forgiveness. It's the only way the docs build can recognize the forward reference.
- there's still many (15) duplicate object description warnings, but I'll defer those

## Changelog description
<!-- Provide a brief single sentence for the changelog. -->

## Status
<!-- Please `poetry install; bash scripts/format.sh` in the base folder. -->
- [x] Code base linted
- [x] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b4c3bd369cb0`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
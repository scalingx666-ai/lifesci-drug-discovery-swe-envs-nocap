# Issue

**Title:** mopac ci lane. pin to qcel 0.25

## Description

<!-- Thank you for your contribution! -->

## Description
<!-- Provide a brief description of the PR's purpose here. -->

## Changelog description
<!-- Provide a brief single sentence for the changelog. -->
- [x] add mopac testing to CI since @awvwgk kindly packaged it
  * forgiving the electonic energy key seems ok since it was dropped here 
  * not too sure about other test loosening
- [x] upcoming changes make it safer to pin tighter to qcel

EDIT:  

## Status
<!-- Please `pip install .[lint]; make format` in the base folder. -->
- [x] Code base linted
- [x] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f72636429453`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
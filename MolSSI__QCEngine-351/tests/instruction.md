# Issue

**Title:** Refactor torsiondrive for easy parallel subclass

## Description

## Description
<!-- Provide a brief description of the PR's purpose here. -->
This PR refactors the running of the optimizations for the torsiondrive procedure into a function that can be easily overridden by users who would like to implement a parallel version. This avoids users having to deal with the inner workings of the torsiondrives and can instead focus on the distribution of the optimization tasks. 

## Changelog description
<!-- Provide a brief single sentence for the changelog. -->
The torsiondrive procedure has been refactored to make it easier for users to implement a parallel version via subclassing and overwriting the `_spawn_optimizations` method.

cc @SimonBoothroyd 

## Status
<!-- Please `pip install .[lint]; make format` in the base folder. -->
- [X] Code base linted
- [x] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `aeead6fa1327`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
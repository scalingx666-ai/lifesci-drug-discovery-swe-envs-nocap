# Issue

**Title:** Add `keep_going` keyword argument to IRC

## Description

This PR does a couple of things:
1) Adds a `keep_going` keyword argument to `IRC`. When `keep_going=True`, if an IRC inner iteration fails, the IRC optimization will print a warning that the trajectory is no longer accurate, but it will continue with the IRC. This helps when people are using IRC as a way of finding connected minima, but they do not care about the entire IRC trajectory.
2) Fixes a bug where creating an `IRC` instance monkey patches the `get_W` method of the base `PES` class, resulting in all subsequent optimizations using that same `get_W` method.
3) Minor code cleanup and type hinting.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9700b5b7753d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
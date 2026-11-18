# Issue

**Title:** add velocity support to extxyz file format

## Description

I've added support for parsing `velo` into atom velocities, which lets users pull the velocities from extxyz files through `frame.velocities()`.  Similarly, if the frame has velocities set then writing will naturally include them in extxyz as `velo:R:3`.

This .

I confirmed that all tests passed, but since I rarely work with c++ the code style/format may not be great. Hopefully its still somewhat useful.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f428beff2848`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
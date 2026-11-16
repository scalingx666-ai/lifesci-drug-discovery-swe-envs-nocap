# Issue

**Title:** Report OpenGL shader program link errors

## Description

A failed program link queried the log as though the handle belonged to an individual shader, leaving the error empty. Query the program log instead. Extracted from #2868.

Validation: the surfaceless EGL regression compiles two shaders with incompatible interfaces and confirms link failure produces a log. ctest -R Rendering-ShaderLink passed (1 test).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `55ecd967dfa8`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
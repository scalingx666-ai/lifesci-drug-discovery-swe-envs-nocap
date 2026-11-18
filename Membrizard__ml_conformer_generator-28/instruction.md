# Issue

**Title:** fix(js): load RDKit in browser and surface load failures

## Description

Pick a Node vs browser default loader so generation no longer silently returns empty when node:module fails in the browser. Introduce RdkitLoadError, rethrow it from mol helpers, document browser setup, and bump to 0.1.1.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `adb6b8a922fd`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
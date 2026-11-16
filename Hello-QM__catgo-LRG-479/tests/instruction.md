# Issue

**Title:** Add molfile open support

## Description

## Summary
  - add a lightweight MDL V2000 molfile parser for .mol/.sdf fallback imports
  - include .mol/.sdf/.mol2 in the desktop file picker
  - use the molfile fallback for pane imports, text edit reparsing, and popout windows

  ## Verification
  - node --experimental-strip-types parser check with a V2000 water sample
  - npx -p typescript@5 tsc --noEmit --strict --target esnext --module esnext --moduleResolution bundler --skipLibCheck
  desktop\lib\molfile.ts

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `326a7d50e9ca`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
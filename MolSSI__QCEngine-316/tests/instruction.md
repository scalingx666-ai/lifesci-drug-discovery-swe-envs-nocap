# Issue

**Title:** mem, thread, disk config

## Description

## Description
Check that the config of each harness is implemented correctly for scratch, memory, and threading.

## Changelog description
<!-- Provide a brief single sentence for the changelog. -->
- [x] add `TaskConfig.scratch_messy` to prevent scratch directory cleanup
- [x] work on passing Config correctly to harnesses
   - [x] ncores, memory, scratch for psi4, cfour, gamess, nwchem
   - [x] Psi4 memory was a little wrong before (GB vs GiB)
   - [x] GAMESS never ran in parallel before
   - [x] most GAMESS parallel algorithms need memddi set, and there's no good predictor for replicated/distributed partition from a fixed total memory from Config.memory. the mem partition can also vary by method/ncores/deriv/module. now implemented is trying a few partitions through the exetyp=check mode to see what passes. this isn't wholly robust b/c there isn't a consistent marker for memory error vs other error. note that even the regex may differ depending on threading because entirely different modules are run within gamess.
- [x] add programs/test_harness_canonical that tests whether Config is observed. some programs I don't have access to may fail.

## Status
<!-- Please `pip install .[lint]; make format` in the base folder. -->
- [x] Code base linted
- [x] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a0a7e756671e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
# Issue

**Title:** [WIP] Fragdb proposal

## Description

This is a work-in-progress to replace the JSON-Lines fragment file with SQLite-based file.

For full details see  .

- The fragment filename (if not given) defaults to "input.fragdb"
  - This applies to `mmpdb fragment` and `mmpdb index`
- The generated SQLite file is about the same size as the uncompressed fragments file (though the fragments file is very compressible.)
- Fragment output time doesn't appear affected (profiling shows at most 1% in sqlite)
- I haven't tested indexing performance
- The "fragments" format is still available, for cross-comparison purposes.
  - That should be removed before the pull request is accepted.
- It removes the (undocumented) fraginfo format.

The current code needs another cleanup pass.

I will first investigate if  simplifies the tedious manual ORM of this work-in-progress.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `29b44a085af3`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
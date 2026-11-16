# Issue

**Title:** Read MOL2 amide bonds without aromatic flags

## Description

Mol2Reader treats Tripos `am` like `ar`, marking ordinary amide bonds and their end atoms aromatic.

Read `am` as a single bond without setting aromatic flags. Continue reading explicit `ar` bonds as aromatic, including the ring C-N bond in aromatic 2-pyridone. Preserve atom flags supplied by other `ar` bonds.

Add acetamide and 2-pyrrolidinone regressions, cover aromatic 2-pyridone using `ar` ring bonds, and extend the existing benzene checks. The pyridone test also checks that the exocyclic C=O bond remains double and non-aromatic and its oxygen remains non-aromatic.

Checked on Linux (Ubuntu 24.04.5, JDK 21, Maven) at `3609bf4556` plus this branch: the module/dependency build passes, `Mol2ReaderTest` passes all 22 tests and `storage/io` all 405. With the production code at `3609bf4556`, the acetamide and 2-pyrrolidinone regressions fail (`expected: <false> but was: <true>`); the 2-pyridone test passes there too, as a compatibility check for `ar` rings.

Prepared with AI assistance (Claude Code and OpenAI Codex).

🤖 Generated with [Claude Code](https://claude.com/claude-code)

https://claude.ai/code/session_01JfvcPZyKcKQUG9fQGYfRMw

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `8c8704e38ca2`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
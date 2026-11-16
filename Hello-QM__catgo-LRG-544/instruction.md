# Issue

**Title:** fix(ci): provision pnpm for download deploy

## Description

Fixes the failed dl.catgo-ucsd.org deployment by provisioning pnpm before cloudflare/wrangler-action runs. Adds a parsed-workflow regression test that fails if pnpm is absent or ordered after Wrangler. Verification: targeted workflow test, complete Node/Worker release suite (50/50), and git diff --check.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `df58576f9efe`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
# Issue

**Title:** fix(deploy): avoid Wrangler workspace install

## Description

## Summary

- deploy all three Cloudflare Workers with pinned Wrangler 4.90.1 via pnpm dlx
- avoid wrangler-action attempting a workspace-root pnpm add
- preserve release-rights evidence bytes on Windows before checkout
- support a Windows-only exact-tag desktop backfill without moving v1.4.6
- pin NOTICE-backed text evidence to LF across platforms
- preserve both the immutable v1.4.6 Tauri workflow trust hash and the reviewed backfill workflow hash
- accept the original failed matrix only through a run-id/tag/commit/job/step-specific v1.4.6 provenance exception

## Root causes

1. wrangler-action inferred pnpm and attempted to add Wrangler at the workspace root; pnpm 10 rejected that with ERR_PNPM_ADDING_TO_ROOT.
2. Windows checkout converted release-evidence files from LF to CRLF; paths and counts stayed correct but both NOTICE-backed manifest hashes changed.
3. The original v1.4.6 Tauri matrix is aggregate-failed even though macOS and Linux succeed; provenance now admits only that exact run when Windows uniquely fails at Verify release rights and all later Windows build/upload steps are skipped.

## Verification

- TDD RED captured Cloudflare, Windows evidence/backfill, immutable trust, and narrow provenance contracts before implementation
- 335/335 Node tests passed
- release-rights verifier passed: 2 ledgers
- legal-distribution verifier passed: 10 contracts and 27 required files
- Wrangler 4.90.1 downloads Worker dry-run passed with the R2 binding
- git diff --check passed
- exact Windows CRLF failure reproduced locally; core.autocrlf=false verified the unchanged v1.4.6 tag successfully

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `06c02979b9e9`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
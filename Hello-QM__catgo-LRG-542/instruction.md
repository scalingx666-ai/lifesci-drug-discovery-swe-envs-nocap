# Issue

**Title:** fix(ci): restore Cloudflare app WASM deployment

## Description

## Summary

- replace the stale `jetli/wasm-pack-action@v0.4.0` installer in the Cloudflare App job with the official current wasm-pack installer already used by the green Tests/HPC workflows
- add a regression test that prevents the unsupported old CLI from returning
- add the approved design for the Cloudflare-hosted, all-platform CatGo download center and Cloudflare-only in-app updates

## Root cause

Main commit `cbda4c7e180c035664031ccd50b7156d506dd758` failed in `Deploy app.catgo-ucsd.org` because the action-provided wasm-pack rejected the canonical build command's `--features` flag. The application/WASM code itself passed the Tests workflow, which installs current wasm-pack through the official installer.

## Verification

- `node --test scripts/__tests__/deploy-cloudflare-workflow.test.mjs scripts/__tests__/build-wasm.test.mjs scripts/__tests__/verify-wasm-artifacts.test.mjs` — 13/13 passed
- `pnpm build:wasm` — scalar ferrox, threaded ferrox, chgdiff, and catrender built successfully
- `node scripts/verify-wasm-artifacts.mjs` — all scalar/threaded and bridge assertions passed
- `git diff --check` — clean

## Follow-up

The download-center implementation will follow the committed design in reviewable TDD commits after this deployment blocker is merged.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `cbda4c7e180c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
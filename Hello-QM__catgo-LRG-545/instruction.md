# Issue

**Title:** fix(ci): retry transient wasm-pack failures

## Description

## Summary
- retry each wasm-pack target up to three times by default
- keep production wasm-opt enabled while recovering from transient Binaryen downloads
- cover retry success and bounded failure with executable fake wasm-pack tests

## Root cause
The Cloudflare app deploy failed while wasm-pack downloaded Binaryen v117 from GitHub. The same resource returned HTTP 200 immediately afterward, so the failure was an external transient rather than a source/build regression.

## Verification
- node --test scripts/__tests__/build-wasm.test.mjs (13/13)
- full Node/Worker regression suite (52/52)
- pnpm build:wasm && node scripts/verify-wasm-artifacts.mjs
- git diff --check

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `efb4ef6b5d45`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
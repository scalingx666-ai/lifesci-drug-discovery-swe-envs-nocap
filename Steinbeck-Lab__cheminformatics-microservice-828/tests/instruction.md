# Issue

**Title:** chore: move Node.js to 26

## Description

## Summary

Moves the Node.js version from 24 (and 20 in the docs workflow) to 26.

- `frontend-test.yml`: Node 24 to 26.
- `deploy-doc.yml`: Node 20 to 26. Node 20 is end of life.
- `frontend/Dockerfile`: build stage `node:24-alpine` to `node:26-alpine`.
- `frontend/vite.config.mts`: vitest workers run with `--no-experimental-webstorage`. Since Node 25, Node has a global `localStorage` that hides the jsdom one and has no methods. This caused `TypeError: localStorage.clear is not a function` in 23 tests. The flag is also valid on Node 24.

Node 26 becomes LTS in late October 2026.

## Verification (local, Node v26.12.0)

- `npm ci`, `typecheck`, `lint` (0 errors), `format:check`: pass
- `npm test`: 17 files passed, 63 tests passed
- `npm run build` and root `npm run docs:build`: pass
- I did not build the Docker image locally. The dev-build workflow builds it.

Independent of #826. Either can merge first.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f00b884352f0`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
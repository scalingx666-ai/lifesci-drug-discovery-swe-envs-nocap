# Issue

**Title:** chore: fix Dependabot security alerts

## Description

## Summary
- **Next.js 16.1.6 → 16.2.1**: fixes CSRF bypass, HTTP request smuggling, disk cache exhaustion, DoS via postponed buffering, dev HMR websocket CSRF
- **npm update**: resolves picomatch method injection and flatted prototype pollution
- **frozen_requirements.txt**: updated all versions to current (numpy 2.4.4, sqlitedict 2.1.0 CVE fix, rdkit-to-params 1.3.9, etc.), removed Python 3.7 backport cruft
- **TS fix**: `VICTOR_TYPES` readonly array was incompatible with Next.js 16.2's stricter type checking

## Test plan
- [x] `npm run build` — clean TypeScript build
- [x] `pytest tests/test_mock.py` — 3/3 pass
- [x] `npm audit` — 0 vulnerabilities

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `bb0ea09a4a7b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
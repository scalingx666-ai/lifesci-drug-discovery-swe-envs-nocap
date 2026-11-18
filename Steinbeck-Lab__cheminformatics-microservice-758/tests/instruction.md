# Issue

**Title:** fix(security): patch all frontend dependency vulnerabilities

## Description

Resolve 7 Dependabot alerts (vite, hono, @hono/node-server) and 5 additional npm audit findings (brace-expansion, flatted, path-to-regexp, picomatch, yaml). Bump vite to ^6.4.2, add overrides for transitive hono/node-server deps, and apply npm audit fix for remaining issues.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `4c7356de8c8e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
# Issue

**Title:** fix(ci): rename REACT_APP_API_URL to VITE_API_URL in Docker build args

## Description

CRA→Vite migration changed env var prefix from REACT_APP_ to VITE_. The CI workflows still passed the old variable name, so the Dockerfile default (localhost:8000) was used instead — causing deployed builds to point API calls to localhost instead of the production/dev API.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e10a5ed9bb13`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
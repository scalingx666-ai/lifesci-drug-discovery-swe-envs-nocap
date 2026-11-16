# Issue

**Title:** fix(mcp): stabilize MCP Docker deployment and document integration

## Description

- Modernize lite image, Java setup, and dependency constraints
- Fix exception registration and cache startup assets
- Expose MCP on port 8002 and remove monitoring services
- Add MCP tool inventory, usage examples, and agent setup guide

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `01e0f60dd043`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
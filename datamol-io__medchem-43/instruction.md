# Issue

**Title:** docs: streamline README/docs and fix release docs alias

## Description

- Streamline README + docs install instructions (core-only, positive framing; drop absence notes and non-core rationale).
- Fix the release \`documentation\` job: delete the legacy standalone \`stable\` version before deploying it as an alias of the release version (mike rejects reusing a version name as an alias).

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d77e67639b62`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
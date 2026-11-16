# Issue

**Title:** feat(catbot): atom-selection DSL for agent-driven selection

## Description

CatBot/MCP-only atom-selection DSL: agent runs e.g. `catgo_view(action="select", query="elem:O AND frac:c>0.9")` to select atoms by text instead of clicking. No user UI.

**Grammar v1**: elem/label/ids/id/pos/frac/bonded/sphere + AND/OR/NOT (& | !) + parens (AND > OR). 0-based indices.

**Files**: `select-dsl.ts` (576, dependency-free total LL parser, depth-guarded, no ReDoS) · `server_claude_code.py` +67 (new `select` action on catgo_view, live Menu-B only, reuses /view/command bus) · `Structure.svelte` +21 (handler → selected_sites, replace/add/subtract).

**Tests**: tests/vitest/select-dsl.test.ts — 54 passing. No new type errors. Adversarial review: ship-worthy.

Grammar adapted from AtomCanvas (MIT).

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `162740544ae8`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
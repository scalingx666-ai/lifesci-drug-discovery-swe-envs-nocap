# Issue

**Title:** fix(alterlab-core): make plugin installable on current Claude Code

## Description

## Problem

`alterlab-core` fails to install on current Claude Code (reproduced on 2.1.187, the latest published release):

> ✘ Failed to install plugin "alterlab-core@alterlab-academic-skills": This plugin uses a source type your Claude Code version does not support. Update Claude Code and try again.

The "update Claude Code" hint is misleading — it fails on the newest release, so updating does not help. Every other `alterlab-*` plugin in the marketplace installs fine.

## Cause

`alterlab-core` is the only plugin whose marketplace entry declares `commands` and `agents` as arrays of sibling-skill subdirectory paths, plus a plugin-level `hooks` reference. The current CLI rejects that manifest shape. The `source` (`./skills/core`, a plain path) and `mcpServers` (`./.mcp.json`) are not the issue — `alterlab-databases` ships the same `mcpServers` file-ref and installs without problem.

## Fix

Conform the `alterlab-core` entry to the proven-working `skills` + `mcpServers` shape (identical key set to `alterlab-databases`). After this:

- The 9 core skills install.
- The 4 research MCP servers (pubmed / openalex / crossref / zotero) install.

The bundled slash-commands, subagents, and the figure-stamp hook are removed from the manifest **for now**. To re-add them the supported way, move the command/agent files to plugin-root `skills/core/commands/` and `skills/core/agents/` (or add a `skills/core/.claude-plugin/plugin.json`) so Claude Code auto-discovers them, instead of cross-referencing sibling skill folders from the marketplace entry.

## Bonus fix

`skills/core/hooks/hooks.json` had a doubled path: `${CLAUDE_PLUGIN_ROOT}` already resolves to `skills/core`, so the hook command pointed at `.../skills/core/skills/core/scripts/stamp_figure.py`, which does not exist. Corrected to `${CLAUDE_PLUGIN_ROOT}/scripts/stamp_figure.py`.

## Verification

The new entry is the same shape as `alterlab-databases`, which installs cleanly on this CLI. Recommend a test install from this branch before merge.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1f0316d90e9e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
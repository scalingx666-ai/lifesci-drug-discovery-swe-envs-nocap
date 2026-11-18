# Issue

**Title:** CLI: read batch and input files saved by Windows PowerShell

## Description

## Summary

Windows PowerShell 5.1 can write text files with a byte-order mark (`Set-Content`/`Out-File -Encoding utf8` writes a UTF-8 BOM; `-Encoding Unicode` writes UTF-16 with a BOM), and the CLI rejected such batch files ("Could not read batch file …"). Found on Windows while running recipe 11.

Every user text file the CLI reads (batch files, document inputs, SMILES lists, the plugin trust file; the MCP server reaches the same readers) now goes through one helper that strips a UTF-8 BOM, decodes UTF-16LE/BE with a BOM, and accepts CRLF line endings. Files without a BOM read exactly as before.

## Files changed

- `packages/chemdraft-cli/src/textInput.ts` (new helper) and its callers: `output.ts`, `documentInput.ts`, `pluginTrust.ts`, `commands/nmr.ts`.
- Tests: `textInput.test.ts`, `textInputIntegration.test.ts`.
- Docs: `packages/chemdraft-cli/README.md`, `skills/chemdraft/references/files.md`.

## Tests run

- `pnpm lint`: pass
- `pnpm vitest run` (full): 308 files, 6132 tests pass

## Platforms

- Windows ✓ (PowerShell 5.1: UTF-8 BOM and UTF-16LE batches render, main exits 2; no-BOM files unchanged; recipe 11's PowerShell block runs clean)
- macOS ✓ (CLI: BOM+CRLF batch renders, exit 0)
- macOS: unchanged behaviour for ordinary files (tests)

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `14459a46f06c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
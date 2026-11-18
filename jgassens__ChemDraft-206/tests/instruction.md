# Issue

**Title:** Make the product page standalone

## Description

## Summary
- The ChemDraft page no longer links to the owner's other website or shows its umbrella brand.
- Brand is now the ChemDraft icon and name. Header nav jumps to sections on the page (Features, AI assistants, Support) plus GitHub. Footer links to the latest release, support and the source.
- Page title and share-card site name are now just "ChemDraft".
- Only `site/index.html` and `site/style.css` change.

## Review
Reviewed by claude-opus (run-20261025-081840-69e2b6): approve. Kimi was skipped because its weekly quota was under 15%.

## Platforms
Web page only, no native code. Not loaded in a browser; checked by reading the diff and searching `site/` for leftover references.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `00a0ce5663e0`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
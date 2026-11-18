# Issue

**Title:** Website: Windows download, beta notice, and AI-assistant section

## Description

## Summary

- **Downloads:** **Download for macOS** (Apple Silicon DMG) and **Download for Windows** (64-bit installer), both resolved from the latest GitHub release, with a fallback to the release page.
- **Beta notice:** a non-dismissible banner at the top, repeated by the downloads: this is a **β test, not an official release**; expect bugs, especially on Windows; report them from the app with **Help ▸ Report a Bug…**.
- **Platform copy:** macOS and Windows throughout, a Windows install note, and the SmartScreen prompt ("More info" → "Run anyway") for the unsigned Windows installer.
- **New section, right after the downloads: "Use ChemDraft from your AI assistant."** The agent skill (merged in #75) for Claude Code, Claude Desktop with MCP, and Codex: what it can do, how it connects (local MCP server and command-line tool sharing the app's document code), and plain requirements (runs from a source checkout, not the downloaded app; Git, Node 24, pnpm 10.12.1, a JDK for name conversion; the NMR plugin is a separate, trusted download).
- **Example gallery** of real prompts and real outputs: "draw a fujita cage structure with chemdraft", and a two-turn brevetoxin B conversation (a Nicolaou-style figure, then a predicted ¹H NMR spectrum, labelled predicted, not measured). Each image opens at full size.

## Verification

- Checked in a browser at desktop and phone widths: both downloads resolve to the v0.3.9 assets, no page-level horizontal scroll at 375 px, and the gallery stacks on phones.
- `node --check site/app.js`; no competitor names in `site/`.
- Reviews: Kimi `site-review1` (downloads and beta notice), `site-review2` (AI-assistant section, every claim checked against the skill's setup guide), `site-review4` (gallery: captions, alt texts, image sizes, NMR honesty); Fable `site-beta7` (alt-text fix). No blockers.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a3db4489e024`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
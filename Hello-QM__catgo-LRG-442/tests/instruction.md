# Issue

**Title:** docs(ios): App Store submission runbook + reusable scripts (no Mac)

## Description

Mac-free flow used to ship CatGo 1.4.0 to the App Store + two reusable scripts (screenshot padding, metadata push via ASC API). Captures the gotchas: cert/secret split (Apple Distribution vs Developer ID), fastlane deliver's review-detail crash → API workaround, globally-unique app name, whatsNew not editable on first release, version-must-match-build. No credentials committed.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `011d02cf5713`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
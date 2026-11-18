# Issue

**Title:** Stress test: close isolation gaps found by the first baseline

## Description

. The first baseline run of the agent-skill stress test showed harness gaps; this fixes them. Test tooling only, under `tools/agent-skill/stress/`.

## Changes

- **Isolation (codex):** each case gets a fake `HOME`, and its ChemDraft skill is a link to the checkout under test (the documented install). Before, the skill was a copy, so its checkout discovery found nothing and agents searched the whole home folder and ran the CLI from other ChemDraft checkouts. The linked skill is scanned for agent instruction files and hashed through nested links.
- **Audit:** any path inside a ChemDraft checkout other than the one under test (absolute, `$HOME`, `%USERPROFILE%`, or `~`/`~/`) fails the case as `isolation-leak: foreign checkout`.
- **Runner:** keeps CLI input files the agent wrote outside its work folder; keeps same-agent completed cases when the usage guard halts.
- **Grader:** canonicalises without 2D depiction (artemisinin made depiction throw); counts text labels that cannot become SMILES (e.g. `CH2OH`) against the agent's structure instead of voiding the case; matches retained files by requested path, canonical path (case-insensitive on Windows, 8.3 names), then unique name.
- README notes on what retention copies and known Windows limits.

## Review

- Kimi K3 (run-20261023-074943-89874): ready to land; its medium finding (`~` not expanded in the audit) is fixed here.
- openai-astra on the skill link and later fixes (run-20261023-081107-c3b7cc, run-20261023-083441-cfd07a, run-20261023-084503-844823): all findings fixed, no new problems.

## Tests

- `pnpm vitest run tools/agent-skill/stress`: 103 passed (macOS)
- `pnpm lint`: clean; `git diff --check`: clean

## Platforms

- macOS: verified.
- Windows: unverified on a Windows host. Junction creation, the fake `USERPROFILE`, and the unprivileged file-symlink skip are covered by platform-parameter tests from macOS; CI's Windows job runs the suite. Whether real `codex exec` on Windows follows the fake home needs one run there.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b1325d561ff2`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
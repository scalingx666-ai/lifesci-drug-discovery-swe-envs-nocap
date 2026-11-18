# Issue

**Title:** Stress test report: allow cause-less accepts, count auto-only failures

## Description

Two fixes to the agent-skill stress test's report step (`tools/agent-skill/stress/grader/`), found while scoring the baseline. Test tooling only.

- **Accepted cases need no cause.** The visual-review instructions ask for a cause only on non-passes, but `report.mjs` rejected any verdict without one, so the first real visual review (13 accepted cases with `cause: null`) could not be reported. Accepts may now have a null or absent cause; rejects still need a valid one. The generated instructions say so.
- **Auto-only failures are counted.** A case whose automatic checks fail while the visual reviewer accepts it is still a fail (the case-result rule in `SCORING.md` is unchanged). It now gets cause `auto-only` with the failed checks listed, its own column in the cause table, and the failed checks named in the worst-failures list. Before, such failures had no cause and fell out of every count.

## Review

openai-astra (Kimi is busy with the visual pass): run-20261023-100720-f4fc43 found the uncounted-failure gap in the first fix; run-20261023-103024-0d7da0 confirms it is fixed with no new problems.

## Tests

- `pnpm vitest run tools/agent-skill/stress`: 109 passed (macOS)
- `pnpm lint`: clean; `git diff --check`: clean

## Platforms

- macOS: verified. Windows: no platform-specific code touched; CI's Windows job runs the suite.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `81024e52b612`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
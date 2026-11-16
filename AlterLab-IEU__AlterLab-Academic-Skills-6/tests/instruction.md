# Issue

**Title:** fix(ci): run behavioral evals on demand only, drop weekly cron

## Description

## Summary

The weekly **Tests** run (`schedule: 0 6 * * 1`, Mondays 06:00 UTC) failed on its first fire after the v2.0 merge ([run 27131344498](https://github.com/AlterLab-IEU/AlterLab-Academic-Skills/actions/runs/27131344498)) — **1080/1080 behavioral evals** errored `claude CLI exited 1`.

**Root cause:** the `behavioral evals (slow)` job shells out to the `claude` CLI for LLM grading, authenticated by `ANTHROPIC_API_KEY`. The repo has **no secrets configured**, so the env var was empty and every invocation exited 1. (Proof: the eval step logged `ANTHROPIC_API_KEY:` empty, not `***`; `gh secret list` returns nothing.) The cron would re-fail and email every Monday.

## Changes

- Drop the `schedule:` trigger from `pytest.yml`; behavioral evals now run on **`workflow_dispatch` only** (they're paid + slow).
- Remove the now-dead `if: github.event_name [!=|==] 'schedule'` guards on both jobs.
- Document that the behavioral job needs the `ANTHROPIC_API_KEY` repo secret.

The fast lane (`lint, compile, schema + eval`) is unchanged and still runs on every push/PR.

## Run on demand

```
gh workflow run pytest.yml --repo AlterLab-IEU/AlterLab-Academic-Skills
```
> Requires setting the `ANTHROPIC_API_KEY` repo secret first, or the behavioral job will fail the same way.

## Test plan

- [x] YAML parses; triggers are now `push, pull_request, workflow_dispatch` (no `schedule`); both jobs intact.
- [ ] After merge: confirm no scheduled run appears next Monday; verify `gh workflow run pytest.yml` dispatches.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3f16b6f6b86f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
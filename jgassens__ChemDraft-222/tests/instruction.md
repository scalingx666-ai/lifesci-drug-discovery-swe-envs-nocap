# Issue

**Title:** Give every dev build one shared app identity

## Description

Branch builds now share the bundle identifier `org.chemdraft.desktop.dev` instead of one per worktree, so a permission granted to the dev app (such as screen control for hands-on tests) carries over between builds. The stable app (`org.chemdraft.desktop`) is untouched, and the worktree label in the title, build stamp and run-app banner is unchanged.

- All dev builds share one app-data folder, so only one runs at a time. `run-app` refuses to launch while another checkout's dev build is running, naming it; it never stops it.
- A machine-wide launch lock (atomic `mkdir`) keeps two checkouts from launching at once; it is held through an interrupted launch (bounded at 60 s) and recovers locks left by a crash.
- Node launchers (used on Windows) use the same shared id.
- AGENTS.md §15.2, README, perf-probe and OCSR fixture docs updated; the OCSR real-engine check accepts the new id.

Known limitation: a reclaim race that needs a SIGKILL during lock takeover plus a second launcher in the same instant is not closed.

Platforms: launcher tests (48) pass on macOS; Windows launcher behaviour covered by platform-mocked tests only, not yet run on Windows.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `caec08a7cdbb`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
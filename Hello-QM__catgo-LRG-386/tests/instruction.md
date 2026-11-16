# Issue

**Title:** fix(hpc): durable SSH sessions + file-browser session recovery

## Description

## Problem
An HPC connection that was still usable (terminal worked, dot green) showed "Session expired" in the Files tab, and refresh didn't help. The user noted CatGo sessions die far sooner than a plain `ssh`/kitty session.

## Causes & fixes

**Durability** — the backend reaped connections aggressively:
- `IDLE_TIMEOUT` was **1h** → idle connections silently closed. Raised to **24h** (`CATGO_HPC_IDLE_TIMEOUT`, `0` = never reap).
- App-level `echo` keepalive marked a connection **dead on a single** failed/slow ping → over-killed on busy login nodes. Now needs a **streak** (`KEEPALIVE_DEAD_AFTER=3`).
- SSH-level keepalive already ran (`keepalive_interval=30`) but used asyncssh's default `keepalive_count_max=3` (90s). Raised to **6** (~3min) so a slow node isn't dropped.

**Recovery** — the terminal self-heals (`pty.ts` finds a live replacement session) but the file browser had none: it kept calling `listFiles()` with the dead id, and refresh re-used it. `FileTree` now fires `on_session_expired`; `ServerPane` re-syncs with the live backend connections, adopts a live session for the same host, and remounts the tree.

## Why it was designed the aggressive way
Resource hygiene (the backend may hold many SSH connections; HPC login nodes cap concurrent sessions and kill idle ones) + fast dead-connection detection so the UI doesn't show zombies. The fixes keep both (keepalive for firewalls, dead-detection) but stop over-reaping sessions the user still relies on.

Type-check clean for changed files; connection_pool.py syntax-checked.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c243b11bb4f9`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
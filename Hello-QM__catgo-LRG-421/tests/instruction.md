# Issue

**Title:** fix(hpc): binary dotfile no longer drops the SSH session ("session expired")

## Description

## Problem
Connecting to a remote whose home contains a non-UTF-8 dotfile (e.g. a binary `.pid` / VESTA lock / `.bak`) showed **会话已过期 / "session expired"** the instant the file browser loaded — but only on some clusters. Reported by a user: lab connects then "秒过期"; Expanse is fine.

## Root cause
On connect, the read-many prefetch runs `head -c N <file>` across a batch of dotfiles in one command. `asyncssh` decodes the command channel as UTF-8; a byte like `0xfd` makes that decode raise, so asyncssh sends a protocol disconnect and tears down the **entire** SSH connection. `connection_lost` marks the session dead, and the next directory listing 404s as "Session not found or expired". Homes that are all-text (Expanse) never hit it — hence it looked connection-specific.

Backend log at the moment of failure:
```
Auth for user … succeeded
Connected to <host>
Command: …head -c 65536 …/.VESTA3-…  (read-many over dotfiles)
Sending disconnect: 'utf-8' codec can't decode byte 0xfd … invalid start byte
SSH connection lost … Marked session … as dead (connection_lost)
```

## Fix
Run the read-many command with `encoding=None` (raw bytes) and decode the output in Python with `errors='replace'`. A binary dotfile now yields replacement chars in that one file's preview instead of killing the connection.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f5c8022b06a2`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
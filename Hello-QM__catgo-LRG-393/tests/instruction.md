# Issue

**Title:** feat(cli): expose the catgo CLI from the bundled app (no pip needed)

## Description

**Problem:** an app-only install has no Python `catgo` CLI. The desktop package ships `catgo-server` (PyInstaller bundle of the whole catgo package) + `catgo` (the GUI binary) + `catgo-agent` — but not the CLI, and `catgo` is the GUI, so `catgo dos/submit/...` isn't available without `pip install`.

**Fix (option B — reuse the existing bundle, no second ~500 MB binary):** `server/main.py` dispatches `catgo-server <subcommand>` (dos/band/cohp/freq/slab/supercell/reticular/convert/inspect/push/pull/submit/campaign/freq-inputs/setup/status/stop) to `catgo.cli:main`. The app spawns the sidecar with **no args** (`shell.sidecar("catgo-server").spawn()`), so the server path is unchanged; `serve` is deliberately not delegated.

Ergonomics: a thin `catgo-cli` wrapper (forwards to catgo-server) wired into the Linux **deb/rpm** at `/usr/bin/catgo-cli` (avoids the `catgo`=GUI name collision); a Windows `.cmd` is provided in `deploy/cli/`. Universal form `catgo-server <subcommand>` works on every platform.

`catgo.cli` is already fully collected by `catgo_server.spec` (collect_submodules('catgo'), 70 refs).

Verified: `catgo-server inspect --help` → catgo CLI; `catgo-server --help` → server argparse (unchanged); tauri.conf.json valid.

Follow-ups (noted, not in this PR): CLI subcommands import the server app module first (works, slightly wasteful); macOS .dmg has no `catgo-cli` wrapper yet (use `catgo-server <cmd>`).

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `42c624c01b4e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
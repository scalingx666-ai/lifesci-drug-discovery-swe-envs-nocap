# Issue

**Title:** feat(cli,release): `catgo view` on packaged installs + v1.4.0

## Description

## Summary

Makes `catgo view` (merged in #425) actually work for users who **installed the desktop app** (no Python / no pip), and cuts the **1.4.0** release across all platforms.

### `catgo view` on a packaged install — 3 blockers fixed
1. **Frozen exe didn't route `view`** → added `view`/`gui`/`nanoparticle` to `_CLI_PASSTHROUGH` in `main.py`, so `catgo-server.exe view …` dispatches to the CLI.
2. **CLI couldn't find the app's backend** (auto-assigned port, not 8000) → the server now writes `~/.catgo/server.port` on **every** startup (was daemon-only) and `ServerLink.discover()` reads it. `_autostart` is also frozen-aware (`-m catgo` fails in PyInstaller).
3. **No `catgo` on Windows PATH** → the NSIS `-setup.exe` installer writes a `catgo` shim into a `cli\` subfolder and adds it to PATH (separate folder so it never collides with the GUI `CatGo.exe`, which Windows resolves first).

Plus: with **no app open**, a packaged `catgo view` now **launches the desktop app** and shows the structure, instead of only spawning a headless backend + browser. (Dev/pip installs keep the headless+browser behaviour.)

### Release 1.4.0
- Version bumped across `tauri.conf.json`, `Cargo.toml`/`Cargo.lock`, `package.json`, download page.
- macOS code-signing + notarization wired into `tauri-build.yml` (reads `APPLE_*` secrets; builds unsigned if absent — you have the Apple Developer account, so add the secrets to enable it).
- Release notes: per-platform install (Windows `-setup.exe` for CLI support + SmartScreen "Run anyway" note, Android APK, iOS TestFlight), 1.4.0 highlights. CHANGELOG entry added.

## Verified
- `catgo view` end-to-end against a backend on a **non-default port (:8765)** found purely via `~/.catgo/server.port` → pushed (79 sites). Dev path unchanged (`_find_gui_app()` → None when not frozen).
- JSON config valid; Python compiles; all version surfaces synced to 1.4.0.

## Needs verification on the built artifact (can't test installers locally)
- The Windows NSIS PATH hook + shim (uses the EnVar plugin Tauri ships) — verify `catgo view` from a fresh terminal after installing the `-setup.exe`.
- macOS signing only activates once the `APPLE_*` secrets are added.

## Note on platforms
Tagging `v1.4.0` builds **Windows/macOS/Linux** (tauri-build.yml). **Android** and **iOS** are separate `workflow_dispatch` workflows — trigger them after tagging.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `cbddb2ca7399`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
# Issue

**Title:** feat(desktop): in-app auto-update (Win/macOS one-click, Linux notify)

## Description

## Summary

Installed desktop builds now notice new GitHub releases and update from inside the app — no manual re-download. Built on **Tauri 2's first-party updater plugin**.

- **Windows / macOS** — one-click: the app downloads the signed updater bundle (progress bar), installs, and relaunches into the new version.
- **Linux** — `.deb`/`.rpm` can't be self-installed by the updater, so the app compares the running version to the latest GitHub release and shows a banner that **opens the download page**.
- **Web / mobile** — fully inert (gated by `is_desktop_tauri()`; the updater/process plugins aren't compiled on mobile).

On launch (desktop only) it checks once after a short delay; a bottom-center banner appears only when a newer version exists.

## What changed

- `tauri.conf.json` — `plugins.updater` (GitHub `latest.json` endpoint + minisign public key), `bundle.createUpdaterArtifacts`.
- Rust — register `tauri-plugin-updater` + `tauri-plugin-process` (desktop-only `#[cfg(desktop)]`); new desktop-scoped capability `capabilities/updater.json`.
- Frontend — `src/lib/update/auto-update.svelte.ts` (store + check/install actions) and `UpdateBanner.svelte`, mounted once at app root. i18n keys (en + zh).
- CI — `tauri-build.yml` passes `TAURI_SIGNING_PRIVATE_KEY` / `_PASSWORD` to `tauri-action`, which signs the NSIS / `.app.tar.gz` updater bundles and uploads `latest.json` to the release.

## ⚠️ Required before this works — two repo secrets

The updater verifies bundles with a minisign keypair. The **public** key is committed in `tauri.conf.json`; the **private** key + password must be added as Actions secrets (Settings → Secrets and variables → Actions):

- `TAURI_SIGNING_PRIVATE_KEY` — contents of the generated private key file
- `TAURI_SIGNING_PRIVATE_KEY_PASSWORD` — its password (empty string if none)

The keypair was generated locally (`tauri signer generate`); the private key lives at `~/.catgo/catgo-updater.key` on the dev machine and is **not** in the repo. Without these secrets the build still succeeds but emits no `latest.json` (no auto-update).

## Caveats

- **macOS Gatekeeper** — this repo currently ships macOS **unsigned/un-notarized**. The updater's own minisign signature is independent and works, but an auto-installed macOS update may still hit a Gatekeeper prompt until Apple notarization is wired.
- **Full-bundle updates** — no deltas; each update re-downloads the whole app (~240MB+ bundled backend).
- Endpoint is the repo's `releases/latest` `latest.json`, so a release must be **published** (not draft) for clients to see it.

## Validation

- `cargo check` — passes (plugin deps resolve, capability schema validates).
- `svelte-check` — new files clean (no new errors).
- End-to-end (a real signed release installing over an older build) is **not** exercised here — needs the secrets + a tagged release.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `550290b13387`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
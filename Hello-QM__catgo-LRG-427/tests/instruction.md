# Issue

**Title:** feat(web): in-app "Get the App" download flow for the static web build

## Description

## Summary

In the web (STATIC_ONLY) build, backend features return *"This feature requires the CatGo desktop app. Visit github.com/… to download."* — but the only path forward was a raw GitHub URL, and many users won't even open GitHub. This adds a download flow that appears **exactly where it's needed**.

## Pieces
- **`DesktopRequiredNotice`** — drop-in replacement for a pane's error `<div>`. When the error is the desktop-required one, it renders a **Download button right next to the red text**; for any other error it's just the plain text. Wired into `DopingPane` (the reported case).
- **`GetAppButton`** — a persistent bottom-right **"Get the App"** pill (web build only), Star-on-GitHub style.
- **`DesktopDownloadModal`** — OS picker (auto-detected from UA):
  - **Windows / macOS / Linux / Android** → fetches the GitHub `releases/latest` API and downloads the matching asset by extension (`.exe/.msi`, `.dmg`, `.deb/.rpm`, `.apk`). Asset names are version-stamped, so matching by extension **always tracks the newest release** — no hardcoded version.
  - **iOS** → opens the **TestFlight public beta** (`testflight.apple.com/join/FdHup5Hz`).
  - API failure / no match → falls back to the releases page.

No auto-popups: the modal opens only from an explicit user click on the inline button or the pill. `STATIC_ONLY` gates the pill; the notice keys off the error-message signature. en/zh i18n in parity.

## Testing
- `svelte-check`: 0 new errors; en/zh `app` keys in parity.
- Verified in a `VITE_STATIC_ONLY=true` dev build: opening the page does **not** pop anything; triggering a backend build feature shows the red error + inline Download button; the pill and button both open the OS-picker modal; OS auto-detect + manual switch; iOS shows "Join TestFlight beta".

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `8c9c8077fd4d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
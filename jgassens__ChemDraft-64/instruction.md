# Issue

**Title:** Windows 0.3.8 update feed (latest.json)

## Description

Updates `latest.json`, the Windows in-app updater feed, from 0.3.7 to **0.3.8**. Merging this is what offers 0.3.8 to installed Windows copies. **Not merged; the owner decides when.**

- **Points at:** https://github.com/jgassens/ChemDraft/releases/download/v0.3.8/ChemDraft_0.3.8_x64-setup.exe. It returns 200 and serves byte-identical content: 64,211,709 bytes, sha256 `47B1D74ACBDF4D764C0EF13E8697A8CA51F12B971A1566202C99F601172B49A7`.
- **Built from:** `6b877fa` (= tag `v0.3.8`, version 0.3.8), with `CHEMDRAFT_STABLE_BUILD=1` and a clean tree. The build printed "Stable build: signing the installer for the in-app updater."
- **Signature:** minisign key ID `7707cfa35d062e59`, which matches `plugins.updater.pubkey` in `tauri.windows.conf.json`. It signs `ChemDraft_0.3.8_x64-setup.exe`.
- **Notes:** the `## Windows` section of the v0.3.8 release page, verbatim. Each claim was checked against the code at `6b877fa` for Windows:
  - Help ▸ Report a Bug… is in the Windows menu.
  - On Windows the mailto draft opens through the URL protocol handler.
  - The panic hook records crashes for the next launch.
- **Smoke test** (the built exe run directly; the 0.3.7 install here is kept as the starting point for the update test): the title is plain "ChemDraft", the version is 0.3.8, and the stamp is `10.3.19.05-opus · … 6b877fa` with no label and no `+dirty`.

**After merging:** the first end-to-end Windows update (installed 0.3.7 → offered 0.3.8) can be tested on the Windows VM.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `cc7140451cd5`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
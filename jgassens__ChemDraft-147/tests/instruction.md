# Issue

**Title:** Add plugin from package reads the picked ZIP's checksum natively

## Description

## Summary

**Plugins ▸ Add plugin from package…** failed with `forbidden path: …\<name>.zip.sha256` on Windows (and on macOS outside existing scopes): the file dialog grants filesystem scope only for the picked `.zip`, so the webview couldn't read the checksum `pnpm plugin:package` writes beside it.

A main-window-only native command, `read_plugin_package`, now reads both without widening the webview's scope:
- opens the ZIP (no-follow on the final component, regular files only), takes the **opened handle's** real final path (`F_GETPATH` / `GetFinalPathNameByHandleW`) and checks *that* against the dialog scope;
- derives `<final long name>.sha256`, opens it the same way and requires the same final parent folder (so Windows 8.3 short names can't skip a present checksum);
- reads both from the validated handles within size caps (32 MB / 4 KB) and returns one binary IPC response (not a JSON number array).

The checksum stays **optional** (ADR-0029 §4): missing → installs, not marked verified; present but bad → refused. All other install gates are unchanged.

Design and threat model: `docs/architecture/plugin-package-reading.md`. Same-user processes racing folder renames during the read are out of scope (they can already read the user's files and replace the ZIP and checksum together).

## Reviews
- Astra round 1: P1 parent-folder swap before open, P2 8.3 alias skipping a present checksum → fixed (handle-based authorization).
- Astra round 2: two residual same-user rename races → ruled out of scope by the master, recorded in the design note.
- Sol: integration, catch-up and docs APPROVE.

## Tests
- macOS: `pnpm lint` ✓; `pnpm vitest run apps/desktop/src/plugins` 558 ✓ (1 skipped); `cargo fmt --check` ✓; `cargo clippy --all-targets -D warnings` ✓; `cargo test plugin_package` 14 ✓ (incl. a deterministic parent swap before open).
- Windows: hands-on run pending (with/without/wrong checksum, 8.3 short name, junctioned folder).
- macOS hands-on: not run (tests, reviews, Windows run and CI).

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b0bf5c749641`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
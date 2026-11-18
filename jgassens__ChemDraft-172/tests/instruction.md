# Issue

**Title:** Windows: make the engine install work for a normal user (junction relocation, venv launcher rewrite)

## Description

## Summary
On Windows, installing the MolScribe recognition engine has never worked for a normal user. This is present in 1.0. Two separate problems in the shared installer (`local_engine`) caused it:

1. **Symlink privilege (os error 1314).** Relocation deleted the directory link uv creates under `python\` and recreated it with `symlink_dir`, which needs Developer Mode or elevation. It is now recreated as a **junction**, as uv made it, through the existing `windows-sys` dependency. Verbatim (`\\?\`) and plain path forms are both matched, and targets are written in plain absolute form.
2. **venv launcher points at the staging dir (os error 2).** uv's Windows `venv\Scripts\python.exe` embeds the absolute base-interpreter path. After the swap it still pointed at `<engine>.partial`, so the post-install check failed. After relocation and before that check, a Windows-only, `--offline` `uv venv --allow-existing --relocatable` re-run against the final tree rewrites it. It goes through the usual child supervision, and the same happens on the upgrade and previous-tree recovery paths. Its scratch uv cache is removed afterwards.

Also: a failed launcher refresh of `engine.previous` no longer blocks a reinstall, and the startup sweep no longer depends on building an HTTP client. Unix behaviour is unchanged.

## Verification
- **Windows, real run** (Explorer launch outside Claude's container; normal user, Developer Mode off, not elevated) on 36241b9d:
  - cargo fmt, clippy `-D warnings`, test 352/352
  - fresh install completes; the link is a junction (tag 0xa0000003) into the final dir, and the launcher embeds the final path
  - recognition of a rendered aspirin returns `CC(=O)Oc1ccccc1C(=O)O` (High Confidence) and inserts
  - quit with the sidecar running leaves 0 python.exe
  - relaunch and Remove engine delete every `ocsr-engine*` dir
  - no console windows seen
- **macOS:** fmt, clippy and the local_engine/ocsr_engine tests. Unix code paths are unchanged.
- **Reviews:** Kimi's first review (run-20261021-140729-7d9877) hit its usage limit and passed to claude-fable, which asked for changes. Later reviews: claude-fable run-20261021-142437-96bc5b (APPROVE), run-20261021-144544-c74ac6 (APPROVE with findings, now fixed), run-20261021-150452-baa992 (APPROVE).

## Known limitations
- Only x64 Windows (`windows-x86_64-none`).
- If a reinstall's refresh of a working previous engine fails for a transient reason, that copy is discarded. If the fresh install then also fails, no engine is left (documented trade-off).
- Upgrade over an existing engine on Windows is covered by tests, not yet by a real run.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2dec5d841967`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
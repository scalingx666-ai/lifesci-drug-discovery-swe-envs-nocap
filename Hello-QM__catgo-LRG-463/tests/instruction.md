# Issue

**Title:** fix(docs): local PDFs/images load via the blank-session read-binary route

## Description

## Symptom

Opening a **local** PDF in the doc viewer shows an empty pane — even after #462's pdf.js renderer. No error, no loading state.

## Root cause

`load_doc_content` hard-returned `{binary: null}` for local-path binary docs, with a comment: "v1 has no local binary read API". The pdf effect then early-returns on empty `binary_data` — silent blank. Remote (HPC-origin) and inline PDFs worked.

## Fix

The limitation is stale since #451: a blank `session_id` maps to the backend's local-filesystem connection in `_get_hpc`, and `/hpc/files/read-binary` uses the same resolver — **verified live** (`{"session_id":"","file_path":<local pdf>}` → base64 + mime). Local binaries now load via `readRemoteBinaryFile('', local_path)`, failure degrades to the previous empty state.

## Tests

`doc-content.test.ts`: the old "degrades gracefully (no endpoint)" case is flipped into a regression test asserting the blank-session call and the returned base64; 6 pass.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `59ce739bdb9a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
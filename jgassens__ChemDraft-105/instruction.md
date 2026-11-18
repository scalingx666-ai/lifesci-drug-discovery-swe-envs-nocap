# Issue

**Title:** Close checkout app before Windows rebuild

## Description

Gracefully close the running ChemDraft debug app from this checkout before Cargo rebuilds it, avoiding executable-lock failures without force-terminating the process.

Windows cleanup now warns "Could not check for a running ChemDraft app; continuing" and continues when PowerShell cannot be spawned or the process check fails. PowerShell uses exit code 2 only when a matching process remains running after WaitForExit(10000); Node maps that case to exit 1. CloseMainWindow() returning false still allows the full wait. Path comparison does not resolve 8.3 short names, subst drives, or junctions. macOS and Linux launch behavior is unchanged.

Validation on Windows:
- `node --check scripts/dev.mjs` and `git diff --check`: passed.
- No app running: executed the actual PowerShell cleanup block; it returned successfully and reached the subsequent startup continuation marker.
- powershell.exe not on PATH: executed the cleanup block with an empty child PATH; it printed the requested warning and reached the subsequent startup continuation marker.
- App running from this checkout (it closes and dev starts): live application/dev startup not tested. A simulated matching process in the actual PowerShell script verified that CloseMainWindow() returning false followed by WaitForExit(10000) returning true allows startup continuation; a simulated process still running after the wait causes Node exit 1.
- Other PowerShell failure: warning and startup continuation verified.

The checks ran the cleanup block in an isolated harness; they did not compile or launch Tauri dev. Full Windows app-close/dev-start integration remains to verify. macOS and Linux runtime checks were not run.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `02da7fbc9add`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
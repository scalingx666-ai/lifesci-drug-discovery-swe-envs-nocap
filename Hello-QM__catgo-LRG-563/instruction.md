# Issue

**Title:** fix(database): restore MP, OPTIMADE, and PubChem search

## Description

## Summary

Restore structure and molecule database search in the web app and VS Code extension after upstream API/provider changes.

## Root causes

- Materials Project's OPTIMADE endpoint currently responds successfully but reports no available structures, while the official Materials Project REST API still returns records.
- Several previously selected OPTIMADE providers are unavailable or expose child implementation URLs that the VS Code backend did not resolve correctly.
- VS Code backend routing treated MPDD as Materials Project and lost pagination metadata.
- PubChem formula/name/element searches did not consistently honor pagination, and cache keys omitted pagination parameters.
- The VS Code webview emitted absolute asset URLs, which resolve against the `vscode-webview://` origin and can return empty WASM responses.

## Changes

- Use the official Materials Project REST summary endpoint when an MP API key is available, including formula/element queries, pagination, totals, and structure conversion.
- Add an MP REST fallback when the MP OPTIMADE endpoint returns no data.
- Update the Python Materials Project router to use current summary fields and exact counts.
- Harden OPTIMADE provider discovery and recovery:
  - resolve child provider URLs;
  - support provider bases that already end in `/v1`;
  - preserve pagination metadata and query options;
  - stop routing MPDD through the Materials Project endpoint;
  - exclude known unavailable providers and avoid permanently caching transient fallback state.
- Fix PubChem cache keys and implement paginated formula/name/element searches.
- Emit relative VS Code webview asset URLs so bundled WASM and worker files load from the extension package.
- Refresh the VS Code lockfile so frozen installs include the declared test/runtime dependencies.

## Validation

- `pnpm test`: 291 test files passed, 1 skipped; 5164 tests passed, 53 skipped.
- `pnpm check`: 0 errors (304 existing warnings).
- `pytest -q server/tests/test_materials_project_router.py server/tests/test_optimade_provider_recovery.py`: 5 passed.
- `pnpm --dir extensions/vscode install --frozen-lockfile`: passed.
- `pnpm --dir extensions/vscode run package`: produced `catgo-1.4.7.vsix`.
- Installed the generated VSIX locally and verified `guangsheng.catgo@1.4.7` is registered by VS Code Server 1.128.1.

## Notes

This branch is based on v1.4.7 and includes the already merged PR #560 scalar ferrox WASM selection. The implementation here does not duplicate that selector; it fixes the remaining webview asset URL and database routing failures.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `8ded15b48f50`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
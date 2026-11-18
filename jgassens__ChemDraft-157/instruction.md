# Issue

**Title:** Windows: plugin workers can start nested module workers

## Description

On Windows, every NMR prediction failed with "The NMR worker crashed (NMR_PROVIDER_FAILURE)". The Windows session traced it: WebView2 aborts the main-script load of a worker started from inside a worker on the app's custom origin (`net::ERR_ABORTED`), even though the app serves the file 200. Starting the same worker from the page works, and so does a blob module that imports the real URL.

- Plugin workers get a small bootstrap shim on Windows: a nested `new Worker(sameOriginUrl, {type: 'module'})` is created from a one-line blob module that imports the real URL, so the script loads through a module import (which WebView2 allows) and `import.meta.url` stays the real URL (relative assets such as the NMR resources still resolve).
- Only same-origin, credential-free module workers on the app origin are wrapped; classic, cross-origin, `data:` and `blob:` URLs pass through untouched. The CSP (`worker-src 'self' blob:`) and plugin permissions are not widened. One nesting level is supported on Windows (documented).
- macOS and the web build are unchanged (platform passed in; both branches tested).

**Reviews:** Kimi (kiminested-20261020) APPROVE, two doc findings being addressed.
**Tests:** lint, 7181 vitest, web build, cargo fmt/clippy/334 tests on macOS.
**Platforms:** Windows hands-on (NMR prediction end to end) pending; macOS NMR to check.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `7f44cecd1d27`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
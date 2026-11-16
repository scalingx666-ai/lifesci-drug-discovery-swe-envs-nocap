# Issue

**Title:** feat(cli): pip-installable catgo — bare `catgo` launches the app, SPA bundled in the wheel

## Description

## Summary

Make CatGo installable from PyPI — `pip install catgo` → `catgo` launches the full app.

- **Bare `catgo`** launches the app: starts the backend and opens the web UI in a browser. The old REPL moved to **`catgo shell`**; new **`catgo app`/`catgo web`** aliases (`--no-browser` to skip).
- **The web UI ships in the wheel.** `scripts/bundle-web.mjs` copies the built SPA (`build-desktop/`) into the package (`server/catgo/web/`, git-ignored); `pyproject` whitelists it as a wheel artifact. `catgo app`/`serve` resolve the bundled SPA and the backend serves it same-origin.
- **Works on any port.** The bundle's compiled API URL is `localhost:8000`, but the backend injects `globalThis.__CATGO_RUNTIME_SERVER__ = location.origin` into the served `index.html` and `api/config.ts` reads it (a dynamic global the bundler can't fold), so the app talks to whatever origin served it — `catgo app --port N` just works even if 8000 is taken.
- **Package renamed** `catgo-engine` → `catgo` (free on PyPI); entry point unchanged. `README-pypi.md` as the long_description. **`pypi-publish.yml`** builds WASM + SPA, bundles it, builds the wheel, twine-checks, and publishes on Release / manual dispatch.

## Verified (locally)
- Wheel `catgo-0.1.0-py3-none-any.whl` (46 MB) bundles `catgo/web` (371 files).
- `catgo app --port 8010` serves the SPA and every `/api` call hits `:8010` (200) — verified in-browser, including a live HPC (SSH) connect and the user's workflows/DB.

## To publish
Add a `PYPI_API_TOKEN` repo secret (or configure PyPI Trusted Publishing — `id-token: write` is set), then cut a Release or run the workflow.

## Notes
- Wheel is ~46 MB (raw SPA 83 MB) — gesture ONNX (~28 MB) + Monaco dominate; a slimming pass can come later.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0649cc8149be`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
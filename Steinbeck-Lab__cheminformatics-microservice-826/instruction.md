# Issue

**Title:** fix(deps): resolve open Dependabot alerts

## Description

## Summary

Resolves all 35 open Dependabot alerts (all npm, in `frontend/package-lock.json` and the root `package-lock.json`).

- **Direct bumps (frontend):** `axios` ^1.20.0, `dompurify` ^3.4.16, `vitest` / `@vitest/coverage-v8` ^4.1.11.
- **Transitive (frontend):** lockfile refreshed so `proxy-addr`, `browserslist`, `baseline-browser-mapping`, `fflate` (0.8.3 and three-stdlib's 0.6.11), `js-yaml`, `@humanfs/node` and `@vitest/mocker` land on patched versions.
- **`postcss-selector-parser`:** `@tailwindcss/typography` pins the vulnerable `6.0.10` exactly, so a scoped override forces `^7.1.6` under it.
- **Removed the `shadcn` devDependency.** It is the component-generator CLI and nothing imports it. It was the only source of `hono`, `fast-uri`, `ip-address`, `@modelcontextprotocol/sdk` and of `braces` (GHSA-vfj7-8cjw-p6xm, which has **no patched release** and was failing the `npm audit --audit-level=low` CI step). Use `npx shadcn@latest add <component>` when adding components. Overrides that no longer match any package were removed.
- **Root:** lockfile refreshed (`nanoid` 3.3.20, `postcss` 8.5.30).

## Verification (Node 24, same as CI)

- `npm audit --audit-level=low`: 0 vulnerabilities (frontend and root)
- `npm run typecheck`, `lint` (0 errors), `format:check`: pass
- `npm test`: 17 files passed, 63 tests passed
- `npm run build` and root `npm run docs:build`: pass

Note: frontend tests fail locally on Node 25 (`localStorage.clear is not a function`), because Node 25's built-in `localStorage` shadows jsdom's. This is not related to this PR. CI uses Node 24.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f2b4c053f9fa`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
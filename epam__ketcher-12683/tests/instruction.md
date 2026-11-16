# Issue

**Title:** #12512 - Teach verify-ketcher the example host pages

## Description

## Summary

`verify-ketcher` knew only `index.html`, so agents missed the other host pages of `example/`. While fixing the Indigo worker timeout (#11988), the agent did not know that `duo` (two editors) and `closable` (Show/Hide) existed. It edited `App.tsx` to fake a second editor, and the user had to point at both pages.

| Change touches | Host page to add to `index` |
|---|---|
| state shared across editors (module cache, struct service, worker) | `duo` |
| mount, unmount, `destroy()`, a resource the editor owns | `closable` |
| layout inside a container | `popup` |

```
.memory-bank/modules/example-app.md   + owner: host pages, page per change, dev vs production
.memory-bank/modules/README.md        + index entry
.memory-bank/invariants.md            + A8: each editor owns its resources
.agents/skills/verify-ketcher/
  features/host-pages.md              + drive.mjs recipes for duo, closable, popup
  features/README.md                  + pointer with the trigger
  SKILL.md                            dev serves only index.html; new commands
  scripts/drive.mjs                   + open --no-ketcher, workers, wait --ms
example/serve.json                    + /closable rewrite
```

Pointers to `example-app.md` where an agent starts work, not only at verification:
- `AGENTS.md`, dev server line: dev serves only `index.html`; the other host pages need a production build.
- `ketcher-flow/shared/RED.md`, step 2: reproduce on the host pages the bug involves.
- `.memory-bank/architecture.md`, Overview: a host may hold several editors and remount them.

Two environment bugs found along the way:
- The dev server serves `/src/index.tsx` for every `*.html` page, so `duo.html` and `closable.html` in dev show the one-editor app. This PR documents it and does not fix it.
- `serve` redirects `/closable.html` to `/closable`, and `serve.json` had no rule for `/closable`, so production served `index.html` there. Fixed.

## Evidence

- **Before:** `curl -sL http://127.0.0.1:4002/closable.html` (production) loads `/static/js/index-*.js`.
  **After:** with the `/closable` rewrite, it loads `/static/js/closable-*.js`.
- **Before:** `curl -H 'Accept: text/html' http://127.0.0.1:4002/{duo,closable,popup}.html` (dev) loads `/src/index.tsx` for each page, so the dev server cannot test them.

### Verified in the app

I ran the new recipes on the production build from branch `11973-refactor-upgrade-vite-to-8-3-1`, which contains the worker fix:

| Recipe | Page | Result |
|---|---|---|
| Duo, no lost replies | `/duo` | pass: `top-toolbar` count 4, `workers` `{created: 2, terminated: 0}`, no `info-modal-window` after `wait --ms 40000`, `errors` empty |
| Closable, release on Hide | `/closable` | pass: `open --no-ketcher`, then 3 Show/Hide cycles; `workers` `{created: 3, terminated: 3}` |
| Closable, Hide right after Show | `/closable` | pass: no dialog after `wait --ms 40000`, `errors` empty |

Popup recipe and remote mode: not run.

On `master`, the Duo recipe shows 1 worker until #11988 merges. A8 describes the target state.

## Merge Danger

**Door:** two-way

Agent docs, the `drive.mjs` test driver, and one rewrite in the example app's `serve.json`. The library packages are not touched.

**Blast Radius:** tiny

`serve.json` affects only `npm run serve:*` for the example app: `/closable` now serves the closable page instead of the main app.

---

Memory bank: `.memory-bank/modules/example-app.md` (new), `.memory-bank/modules/README.md`, `.memory-bank/invariants.md` (A8), `.memory-bank/architecture.md` (Overview)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `84a4f6c6b9dc`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
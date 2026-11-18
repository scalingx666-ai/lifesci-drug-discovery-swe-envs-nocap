# Issue

**Title:** Warm the cage paste test's worker before its timed paste

## Description

## Summary

Test-only. `cagePasteQuality.test.ts` › "repairs the cage through the real worker transport within its layout deadline" failed twice on 2026-11-01 on slow Windows CI runners (main run 41328450374, passed on rerun; #243 run 41334012517): it expected 0 atom and label defects and got 11. The cage's repair missed the 2000 ms layout deadline, so the worker client published the unrepaired standard layout. On a cold worker most of that time is first-time loading, not layout: the timer starts once the worker reports ready, and the repair path then imports OpenChemLib's relayout, the shared document workflow and the RDKit relayout entry for the first time, inside that 2000 ms (on this Mac a cold layout phase takes 353 to 490 ms and a warm one 146 to 161 ms).

- **Warm before timing.** The test-only Node transport (`apps/desktop/src/test/depictionNodeClient.mjs`) gains `createNodeDepictionClient({ warmupSmiles, holdFirstResult, deadlineMs })`. With `warmupSmiles`, each new worker runs one full paste of that SMILES before the client sees ready, so the warm-up counts against the 10 s startup budget, and the timed paste then runs on a warm worker under the production 2000 ms deadline. The timed test keeps both of its assertions and now also requires the warm-up itself to finish without warnings. The default `depictSmilesOffThread` export used by other tests is unchanged.
- **Deadline fallback, tested on purpose.** A new test holds the first worker's final result, so the fallback happens every time rather than by timing luck. It checks the published layout is the unrepaired standard cage (hard contacts kept) with the exact production warning, and that the next paste on the same client gets a fresh worker and a repaired cage.
- `DEPICTION_DEADLINE_MS` and all product code are unchanged.

## Does a real user's first cage paste on a slow PC miss too?

Very likely yes, on a slow enough PC. In the app the worker posts ready after RDKit's WASM and OpenChemLib have started, and the 2000 ms layout timer starts then. The first cage paste on that worker still has to load the repair path (OpenChemLib's relayout, the shared document workflow and the RDKit relayout entry) and run the repair inside those 2000 ms. On this Mac that cold layout phase took 353 to 490 ms (3 runs, worker startup excluded) and a warm one 146 to 161 ms, so a machine about four times slower, like the Windows runners that failed today, gets the standard cage with the warning "2D depiction exceeded its 2000 ms layout deadline; used the standard layout."

It can also repeat: a missed deadline kills the worker, so the next paste starts cold again, and a worker left idle for 60 s is evicted, so a paste after a pause is cold too.

**Follow-up (not in this PR):** load the repair path's engines before the worker reports ready (or warm the worker when the app starts), so the 2000 ms covers only layout and repair. This PR does not change that behaviour, and no test now covers a cold worker's first-request time in the app.

## Test expectation changes (existing tests)

| Test | Change | Reason |
|---|---|---|
| `apps/desktop/src/cagePasteQuality.test.ts`, "repairs the cage through the real worker transport within its layout deadline" | Uses a client that warms its worker with the cage before the timed paste; adds an assertion that the warm-up had no warnings. Both original assertions are unchanged | The timed paste measured cold module and engine loading, which a slow runner can push past 2000 ms; it now measures the repair it is meant to check |

## Tests run

On macOS, at `9f4fd3ea`:

- `pnpm exec vitest run apps/desktop/src/cagePasteQuality.test.ts packages/rdkit-adapter/src/depictionWorkerClient.test.ts apps/desktop/src/depiction2d/client.test.ts`, three times in a row: 3 files, 40 tests passed each time
- `pnpm lint`: not run locally; CI's Linux job runs the same root type check
- `git diff --check 97d9bd93 HEAD`: clean

Review: run-20261101-122011-4624d5 (Opus, low), the whole change: no blocking findings. Two low notes, both recorded above or below: the timed test no longer covers a cold worker's first-request time (see the follow-up), and the warm-up now runs inside the transport's 10 s startup budget, so a very slow runner could fail with a startup-deadline error (a loud failure, not a hidden one; the warm-up took under 0.5 s here). One nit declined: `onWarmup` also receives the warm-up's duration, which no test reads; it is kept for diagnosing a slow runner.

## Platforms

- **macOS:** the targeted tests (see Tests run).
- **Windows:** CI only. Test-only change with no platform branch; the point of the change is that the Windows runner's speed no longer decides the result.

Build stamp: `11.01.12.20-codex`.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `97d9bd930abd`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
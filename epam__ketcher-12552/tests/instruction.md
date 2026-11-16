# Issue

**Title:** #12553 - Recognize fails when Indigo apiPath contains explicit port

## Description

## How the feature works? / How did you fix the issue?

`parametrizeUrl()` (`packages/ketcher-core/src/infrastructure/services/struct/remoteStructService.ts:73-75`) used `/:(\w+)/g`, so any `:word` token was treated as a placeholder — including numeric port values in `apiPath` (e.g. `http://127.0.0.1:9321/v2/`). `:9321` was consumed as placeholder `9321`, looked up in `params` (missing) and replaced with `undefined`, producing `http://127.0.0.1undefined/v2/imago/uploads/<id>`.

`request()` only calls `parametrizeUrl` when `method === 'GET' && data` (line 85). The only such call is the Imago status poll inside `recognize()` (`imago/uploads/:id`, line 400); `info()` is GET without payload and all other operations go through `indigoCall('POST', ...)`. As a result only **Recognize** broke while drawing and all other Indigo features continued to work. The bug only manifests when `apiPath` contains an explicit port (e.g. `http://localhost:8000/v2/`); the default `example/.env` uses a relative path `/v2`, so it was not caught by CI.

Fix: match only named placeholders starting with a letter or underscore (`:([A-Za-z_]\w*)`), and leave unknown/`undefined`/`null` placeholders intact to avoid emitting `undefined`. Added a regression test (`packages/ketcher-core/src/infrastructure/services/struct/__tests__/remoteStructService.test.ts`) that calls `recognize()` through the public API with `apiPath = 'http://127.0.0.1:9321/v2/'` and a stubbed `fetch`.

**Before (from the new test):**
```
Expected: "http://127.0.0.1:9321/v2/imago/uploads/abc"
Received: "http://127.0.0.1undefined/v2/imago/uploads/abc"
```
**After:** passes.

### Verification
- `npm run test:unit -w ketcher-core` → 51 suites passed, 494 tests passed
- `npm run test:types -w ketcher-core` → clean
- `npm run test:eslint:quiet -w ketcher-core` → clean
- `npm run test:prettier -w ketcher-core` → clean

## Check list
- [x] unit-tests written
- [ ] e2e-tests written
- [ ] documentation updated
- [ ] PR name follows the pattern `#1234 – issue name`
- [x] branch name doesn't contain '#'
- [ ] PR is linked with the issue
- [x] base branch (master or release/xx) is correct
- [ ] task status changed to "Code review"
- [ ] reviewers are notified about the pull request

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `48af1b20d586`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
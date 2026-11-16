# Issue

**Title:** fix(downloads): return correct status for complete R2 reads

## Description

## Summary
- return 200 for ordinary GETs even when R2 reports a full-object range
- keep 206 tied to a validated Range actually sent to R2
- build partial headers from the GET response metadata and reject malformed upstream partial metadata with 502

## Root cause
R2 may populate `R2Object.range` with `{offset: 0, length: size}` for a complete read. The Worker treated any populated object range as proof that the client requested a partial response, so `/` and `/latest.json` returned 206 without a Range request.

## TDD and verification
- RED→GREEN: full-object R2 range without client Range returns 200
- RED→GREEN: HEAD→GET shrink uses returned range metadata
- RED→GREEN: missing/invalid partial metadata cancels the body and returns 502
- Worker 17/17
- full Node/Worker 55/55
- Downloads Wrangler dry-run
- two review rounds; final review clean

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `394aa0e0dccb`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
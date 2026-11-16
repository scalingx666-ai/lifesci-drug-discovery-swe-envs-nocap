# Issue

**Title:** Write records to cache immediately

## Description

## Description
When fetching records via the cache, records were not written immediately to the cache. Instead, the cache was hooked up via the writeback mechanism.

This was way too slow, especially for complicated records like torsiondrive. So now we write them immediately. Records currently don't have proper change tracking, so any modifications to the record won't be reflected in the cache, but that should be added someday.

## Status
- [X] Code base linted
- [X] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `eea42a788db6`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
# Issue

**Title:** Refactor dataset upload

## Description

## Changelogs

- Refactored `PolarisHubClient.upload_dataset` to fix the 

---

Instead of uploading the file by `follow_redicrect` to the Hub, it's handled manually.  A table content URL (cloudflare) is retrieved by an empty PUT request to the hub.  Then together with the URL, the method, and any additional headers,  the upload request is made to sends the file content along.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `283fb486c710`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
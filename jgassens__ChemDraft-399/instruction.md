# Issue

**Title:** Prepare 1.2.0 version and platform release notes

## Description

Prepares the final desktop 1.2.0 version fields, build stamp, and three platform release-note files on top of batch 4 (#398). The notes cover #395–#397 and omit the unsupported blanket brackets warning and unpublished NMR deuterium claim.

Independent review: google-argon, run-20261113-145425-3a1231. The final tree is identical to the reviewed tree. Existing local validation passed; this draft runs CI on the final prepared candidate.

Do not merge until the remaining native charge checks pass on Mac and Windows and batch 4 lands. This PR does not publish artifacts or update feeds. Final signing, release publication, and the merge to main remain separate release gates.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `7af7e6be08a8`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
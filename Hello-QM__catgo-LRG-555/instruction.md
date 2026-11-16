# Issue

**Title:** fix(release): parse current Android signer output

## Description

## Summary
- accept current and legacy apksigner certificate digest labels
- normalize and deduplicate every reported signer certificate SHA-256
- fail closed unless exactly one valid signer remains and matches repository policy

## Root cause
Android build-tools 37 reports V3.0 Signer instead of the legacy Signer #1 label. The signed APK was valid and matched policy, but the label-specific parser returned an empty digest.

## Verification
- failing run 30211818453 proves v2/v3 signatures and the approved digest
- 12/12 targeted release workflow tests pass
- 329/329 complete Node script tests pass
- current and legacy sample output normalize to one approved digest
- independent review: PASS

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1e4e4995639a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
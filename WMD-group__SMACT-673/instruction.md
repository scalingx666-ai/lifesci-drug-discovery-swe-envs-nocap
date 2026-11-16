# Issue

**Title:** docs: sync .zenodo.json author list with joss/paper.md

## Description

## Summary
- \`.zenodo.json\` was missing Masahiro Negishi and most author ORCIDs, out of sync with \`joss/paper.md\` and the already-fixed \`CITATION.cff\` (#671)
- This is what Zenodo's GitHub integration reads to prefill archive metadata, so worth fixing ahead of archiving the v4.0.1 release for JOSS (openjournals/joss-reviews#11015)

## Test plan
- [x] Validated as JSON
- [x] Diffed against joss/paper.md author/ORCID list

<!-- This is an auto-generated comment: release notes by coderabbit.ai -->

## Summary by CodeRabbit

* **Documentation**
  * Updated publication metadata with additional contributor information and ORCID identifiers for listed creators.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0582aaf9fa91`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
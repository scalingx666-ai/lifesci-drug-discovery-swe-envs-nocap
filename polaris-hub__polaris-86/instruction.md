# Issue

**Title:** Updating column adapter logic and usage

## Description

## Changelogs

- Updated the attribute name in the BaseArtifactModel which indicates the current Polaris client version from `version` to `polaris_version`
- Fixed column adapter logic by introducing a conversion map and updating how the conversion is applied on dataset retrieval

---

_Checklist:_

- [X] _Was this PR discussed in an issue? It is recommended to first discuss a new feature into a GitHub issue before opening a PR._
- [X] _Write concise and explanatory changelogs above._
- [X] _If possible, assign one of the following labels to the PR: `feature`, `fix` or `test` (or ask a maintainer to do it for you)._

---

_discussion related to that PR_

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c1c8958d0928`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
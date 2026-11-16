# Issue

**Title:** Adding a loading indicator for upload/download operations

## Description

## Changelogs

- Using the `yaspin` [package](https://github.com/pavdmyt/yaspin), this PR adds a loading indicator to all client side upload/download operations. 
- The indicator will update to a success or failure status depending on the outcome of the given method that is running. This required wrapping numerous client methods in try/except blocks. 

---

_Checklist:_

- [x] _Was this PR discussed in an issue? It is recommended to first discuss a new feature into a GitHub issue before opening a PR. [Link to issue](https://github.com/orgs/polaris-hub/projects/2?pane=issue&itemId=70508095)_ 
~- [ ] _Add tests to cover the fixed bug(s) or the newly introduced feature(s) (if appropriate)._~
- [x] _Update the API documentation if a new function is added, or an existing one is deleted._
- [x] _Write concise and explanatory changelogs above._
- [x] _If possible, assign one of the following labels to the PR: `feature`, `fix`, `chore`, `documentation` or `test` (or ask a maintainer to do it for you)._

---

NOTE: While the `tqdm` package is already a dependency of `polaris-lib`, the lift required to implement it given the current time crunch is too high. We should however revisit this if we want to have slightly fancier messaging for users. A ticket will be created for this shortly.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b893f8ec2ca5`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
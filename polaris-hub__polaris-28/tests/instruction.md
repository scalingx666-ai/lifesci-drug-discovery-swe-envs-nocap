# Issue

**Title:** feat: Additional model typing to match Hub API

## Description

# Description

This PR adds additional typing on the `BenchmarkResult` and `BenchmarkSpecification` Pydantic models, to match what was defined in the Hub API. We could broaden the accepted types on the Hub (in `user_attributes` for example), as long as we agree on a defined set of types the Hub can validate.

I'm also proposing that the `Metrics` class become an enumeration. While this is less flexible for extension, it allows for much better model validation and it solves an important issue when uploading/downloading artifacts from the Hub: what to do with unrecognized metrics. I'm very happy to discuss this further and see if there's a better way to achieve our goals, so look at this as a conversation starter,  no something set in stone.

# Links
- Hub API PR here: 


_Checklist:_

- [X] _Was this PR discussed in an issue? It is recommended to first discuss a new feature into a GitHub issue before opening a PR._
- [ ] ~Add tests to cover the fixed bug(s) or the newly introduced feature(s) (if appropriate).~
- [ ] ~Update the API documentation if a new function is added, or an existing one is deleted.~
- [X] _Write concise and explanatory changelogs above._
- [X] _If possible, assign one of the following labels to the PR: `feature`, `fix` or `test` (or ask a maintainer to do it for you)._

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e88d206aa3e6`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
# Issue

**Title:** feat: Support result upload for XL benchmarks

## Description

## Changelogs

- Update the `upload_results` client method to us the new V2 API endpoint in the Hub
- Tighten types in Pydantic models to reflect the data structure once parsing is complete
- Update client base request method to return the httpx response, in order to make headers accessible.

## Linked issues

- Closes [PRO-175]

---

_Checklist:_

- [X] _Was this PR discussed in an issue? It is recommended to first discuss a new feature into a GitHub issue before opening a PR._
- [ ] ~_Add tests to cover the fixed bug(s) or the newly introduced feature(s) (if appropriate)._~
- [ ] ~_Update the API documentation if a new function is added, or an existing one is deleted._~
- [X] _Write concise and explanatory changelogs above._
- [X] _If possible, assign one of the following labels to the PR: `feature`, `fix`, `chore`, `documentation` or `test` (or ask a maintainer to do it for you)._

---

This PR updates the client to use the new V2 API endpoint for results. This will enable uploading supports for the upcoming V2 Benchmarks. Due to the nature of the result model in the client, which holds
their related benchmark identitifer but not an object reference, the same endpoint must accomodate both V1 and V2 benchmarks.

I also took the opportunity to tighten the typing in some Pydantic models. We had initially typed our models liberally, to show what could be accepted as inputs. While this still holds, the reality is that
our models normalized these input values to one representation. The updated model typing represents that normalized representation.

The new V2 result endpoint also now returns a [Content-Location](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Content-Location) response header, which will provide the URL of the result on the
Hub. To leverage this, I exposed the full response object to the calling functions, instead of only the JSON body.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5b3e9f629d68`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
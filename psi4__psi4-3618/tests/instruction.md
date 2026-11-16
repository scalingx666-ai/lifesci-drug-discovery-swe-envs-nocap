# Issue

**Title:** Try to fix PR labeling workflow by giving it PR write permission

## Description

## Description
<!-- Provide a brief description of the PR's purpose here. -->
The recently merged PR labeling workflow fails with what looks like a permission error.
`github.GithubException.GithubException: Resource not accessible by integration: 403 {"message": "Resource not accessible by integration", "documentation_url": "", "status": "403"}`
Based on Claude output, this could be resolved by giving the workflow PR write permissions.

## User API & Changelog headlines
<!-- A bullet-point format description of how this PR affects the user.
     This is destined for the release notes. May be empty. -->
- [x] None

## Dev notes & details
<!-- A bullet-point format description of what this PR does "at a glance."
     Target audience is code reviewers and other devs skimming PRs.
     Should be more technical than user notes. Should never be empty. -->
- [x] Changes the permissions of the review-queue GHA workflow for the `pull-requests` scope from read to write.

## AI
<!-- Briefly describe where AI contributed to the PR (tests, derivation,
     bug-seeking, code generation, docs, etc.). No restrictions, but a
     person should be submitting the PR and (as usual) be ready to answer
     questions about it. -->
- [X] LLMs were used to analyze the log of failed workflow runs and suggest a solution.

## Checklist
- [x] No new features
- [x] No docstring or narrative docs/sphinxman/source update needed
- Test running is well covered by CI. For running locally, see [All or relevant fraction of full tests run](http://psicode.org/psi4manual/master/build_planning.html#how-to-run-a-subset-of-tests)

<!--
## HOW TO GET REVIEWED!

- Ready for review -- issue a PR comment with `/review-ready` as sole text to add a "review-requested" label. Expect reviewers to rm this label and add "awaiting-author-contribution". Re-add label for another cycle.
- Priority review -- issue a PR comment with `/review-next` as sole text to add a "review-this-pr-of-mine-next" label to signal priority for attention. Adding will rm it from your other PRs.
- Ready for merge -- use Draft/Open GitHub status to signal your view on merge readiness.
-->

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1ea3b9552909`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
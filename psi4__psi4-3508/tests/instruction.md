# Issue

**Title:** Add workflow to manage PR labels via comments

## Description

This workflow manages PR labels based on comments, allowing users to request reviews or prioritize their PRs. It includes security checks for command usage and limits the number of queued labels based on user roles.

## Description
<!-- Provide a brief description of the PR's purpose here. -->
All the PRs are great, but I feel like I'm reviewing whatever shiny thing I saw last, and I know I've lost track of what are important and ready in some PR stacks. This is an effort (with labels borrowed from c-f staged-recipes) to better see what's priority.


## Dev notes & details
<!-- A bullet-point format description of what this PR does "at a glance."
     Target audience is code reviewers and other devs skimming PRs.
     Should be more technical than user notes. Should never be empty. -->
- [x] each user can issue ~`/please-review-next`~ `/review-next` and that'll get a label (max one per user, so adding bumps it from any other PR). those who handle PRs for other can ask to be added to a 2-allowed list. this is only a starting config.
- [x] if a PR is ready for reivew, add ~`/please-review`~ `/review-ready` to mark as such. these are unlimited. when a reviewer kicks it back, they'll add `awaiting-author-contribution` label (EDIT: and remove `/review-ready`). when ready for re-reivew, redo ~`/please-review`~ `/review-ready`.
- [x] the "concurrency" bit is separate and is supposed to kill the Eco GHA when a newer commit is pushed to a PR. Azure does this automatically, but we've had pileups of Eco's running on the same PR where the newest (and desired) commit can't run until old Mac lanes finish. This is different from "fail-fast" that kills lanes in the same run when one fails.

## Questions
<!-- Any questions or decision points on which you need clarification
     from the Psi4 team. -->
- [ ] thoughts from reviews and reviewees?

## AI
<!-- Briefly describe where AI contributed to the PR (tests, derivation,
     bug-seeking, code generation, docs, etc.). No restrictions, but a
     person should be submitting the PR and (as usual) be ready to answer
     questions about it. -->
- [x] AI usage -- AI Mode of google.com

## Checklist
- [x] ADD SOMETHING TO CONTRIBUTING.md
- [ ] Docstring or narrative docs/sphinxman/source updated if needed
- Test running is well covered by CI. For running locally, see [All or relevant fraction of full tests run](http://psicode.org/psi4manual/master/build_planning.html#how-to-run-a-subset-of-tests)

## Status
- [x] Ready for review
- Ready for merge -- use Draft/Open GitHub status to signal your view on merge readiness

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `90ff9845c10c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
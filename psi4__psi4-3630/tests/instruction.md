# Issue

**Title:** Fix CI since conda dropped from Azure image

## Description

## Description
Fixed broken azure linux lanes.

## Dev notes & details
<!-- A bullet-point format description of how this PR affects the user.
     This is destined for the release notes. May be empty. -->
- [x] suppress linux memory_profiler cases that have turned flaky with clang_latest. It popped up in another Azure linux lane later, so I'm avoiding it everywhere.
- [x] later 3 lanes reliably failed early, and it seems that trial 26.04 image removed a pre-avail conda. so we add it deliberatly and adjust paths
- [x] some of the lanes were still pinned to 22.04, which seems likely to age-out, so update them all to latest. This makes clang-15 unavailable (2022) but we're already testing clang-17 (2023), so I actually made it clang-21 to match its name.
- [x] gcc_latest was running out of memory so ~dial down its unity build size~ turn off unity build and parallelism by going to Makefile generator. It seems to have to do with gcc15 that 26.04 brings. I dialed back to 24.04 (gcc13) to get it to build, as least for now. The L2 2.13 PR has some additional controls I can try.
- [x] in the midst of Azure problems, GHA Eco started failing b/c v2.14 L2 packages are in the middle of building and they need `libint-cxx-devel` instead. So pinning to 2.13 for now.

## AI
<!-- Briefly describe where AI contributed to the PR (tests, derivation,
     bug-seeking, code generation, docs, etc.). No restrictions, but a
     person should be submitting the PR and (as usual) be ready to answer
     questions about it. -->
- [x] AI diagnosed the 26.04 problem and proposed miniforge

## Checklist
- ~Tests added for any new features~
- ~Docstring or narrative docs/sphinxman/source updated if needed~
- Test running is well covered by CI. For running locally, see [All or relevant fraction of full tests run](http://psicode.org/psi4manual/master/build_planning.html#how-to-run-a-subset-of-tests)

<!--
## HOW TO GET REVIEWED!

- Ready for review -- issue a PR comment with `/review-ready` as sole text to add a "review-requested" label. Expect reviewers to rm this label and add "awaiting-author-contribution". Re-add label for another cycle.
- Priority review -- issue a PR comment with `/review-next` as sole text to add a "review-this-pr-of-mine-next" label to signal priority for attention. Adding will rm it from your other PRs.
- Ready for merge -- use Draft/Open GitHub status to signal your view on merge readiness.
-->

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `64fc54046ff5`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
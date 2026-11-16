# Issue

**Title:** analytic D3 Hessian. misc.

## Description

## Description
<!-- Provide a brief description of the PR's purpose here. -->


## User API & Changelog headlines
<!-- A bullet-point format description of how this PR affects the user.
     This is destined for the release notes. May be empty. -->
- [x] D3 Hessian requests now go upstream for analytic, not findif w/i Psi4
- [x] Empirical Dispersion findif Hessians w/i Psi4 now compute rotational dof, not assume stationary, as was probably a bug.
- [x] ZLP functional back to LDA

## Dev notes & details
<!-- A bullet-point format description of what this PR does "at a glance."
     Target audience is code reviewers and other devs skimming PRs.
     Should be more technical than user notes. Should never be empty. -->
- [x] Clear out testing old dftd3+gcp from the psi4 channel. This does leave a number of ne'er run tests, but the old interfaces are deprecated and I don't like to delete correct answers.
- [x] Some diagnostics for the request-review labels
- [x] s-dftd3 1.6 can do analytic d3 Hessians, so add that here. QCEngine 0.52 is going to be required anyways for ECPs.
- [x] ZLP functional was getting defined twice (there's a lda and a mgga in libxc), but the active one p4 can't run anyways.

## AI
<!-- Briefly describe where AI contributed to the PR (tests, derivation,
     bug-seeking, code generation, docs, etc.). No restrictions, but a
     person should be submitting the PR and (as usual) be ready to answer
     questions about it. -->
- [x] AI usage: Opus 5.5 did the Hessian logic at my instruction. Sol noticed the double ZLP

## Checklist
- [x] Tests added for any new features
- ~Docstring or narrative docs/sphinxman/source updated if needed~
- Test running is well covered by CI. For running locally, see [All or relevant fraction of full tests run](http://psicode.org/psi4manual/master/build_planning.html#how-to-run-a-subset-of-tests)

<!--
## HOW TO GET REVIEWED!

- Ready for review -- issue a PR comment with `/review-ready` as sole text to add a "review-requested" label. Expect reviewers to rm this label and add "awaiting-author-contribution". Re-add label for another cycle.
- Priority review -- issue a PR comment with `/review-next` as sole text to add a "review-this-pr-of-mine-next" label to signal priority for attention. Adding will rm it from your other PRs.
- Ready for merge -- use Draft/Open GitHub status to signal your view on merge readiness.
-->

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1ea3b9552909`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
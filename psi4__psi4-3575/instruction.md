# Issue

**Title:** cutting edge QCFractal

## Description

## Description
<!-- Provide a brief description of the PR's purpose here. -->


## Dev notes & details
<!-- A bullet-point format description of what this PR does "at a glance."
     Target audience is code reviewers and other devs skimming PRs.
     Should be more technical than user notes. Should never be empty. -->
- [x] ~There was a sqlalchemy update that Ben has fixed QCFractal for but it won't be released for another day or so. I think pulling qcf from repo will fix our CI. Linux had previously been pulling from repo (to test cutting edge qcf) and mac from package (to test released qcf), so that explains our CI breakage pattern.~
- [x] go back to testing both latest-release and upstream master for QCFractal to get prewarning of impending breakages
- [x] start a py315 lane -- had to skip the conda-tree analysis but that's minor
- [x] use packaged v0.71 qcfractal once released. In practice to continue to allow py310 to work, I set it to v0.70

## AI
<!-- Briefly describe where AI contributed to the PR (tests, derivation,
     bug-seeking, code generation, docs, etc.). No restrictions, but a
     person should be submitting the PR and (as usual) be ready to answer
     questions about it. -->
- [ ] AI usage -- none, for once!

## Status
- [x] Ready for review
- Ready for merge -- use Draft/Open GitHub status to signal your view on merge readiness

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `da101ee409fc`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
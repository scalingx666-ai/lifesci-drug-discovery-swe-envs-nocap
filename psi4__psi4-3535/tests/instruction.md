# Issue

**Title:** Stop fetching SciPy's objects.inv every time our Docs CI lane runs

## Description

## Description
<!-- Provide a brief description of the PR's purpose here. -->
The docs GHA lanes (docs-pr.yml on every PR and merge group, docs.yml on every push to master) currently download https://docs.scipy.org/doc/scipy/objects.inv on every run, putting load on their servers, which they seem to have trouble keeping online. Also, the CI lane fails when scipy servers are down or busy,

The cause is the intersphinx mapping in conf.py.in, whose entries all pass None as the second tuple element, meaning "no local inventory, go and download the <base_url>/objects.inv at build time". Nothing supplies a local inventory, and the CI builds into a fresh objdir on an ephemeral runner with no cache step, so Sphinx's own 5-day inventory cache never survives and every run starts cold.

This entire fuss is going on for the sake of _one_ cross-reference in the whole manual: :func:`scipy.linalg.block_diag` in the block_diagonal_array docstring, which reaches the manual via `automodapi:: psi4.driver.p4util`. Every other scipy mention in the tree is a function-body import, an error string, commented-out test code, or a bare URL, none of which produce an xref. So drop the role in favour of an explicit external hyperlink, which reads the same and needs no inventory, and drop the mapping entry with it.

## User API & Changelog headlines
<!-- A bullet-point format description of how this PR affects the user.
     This is destined for the release notes. May be empty. -->
- No impact

## Dev notes & details
<!-- A bullet-point format description of what this PR does "at a glance."
     Target audience is code reviewers and other devs skimming PRs.
     Should be more technical than user notes. Should never be empty. -->
- [x] Remove scipy from intersphinx mappings to avoid having to web fetch from docs.scipy.org every time our CI runs
- [x] Replace xref with url in the docs

## AI
<!-- Briefly describe where AI contributed to the PR (tests, derivation,
     bug-seeking, code generation, docs, etc.). No restrictions, but a
     person should be submitting the PR and (as usual) be ready to answer
     questions about it. -->
- [x] The commit and the intitial version of the PR description was LLM-generated

## Checklist
- [x] No new features
- [x] PR is a docs update
- Test running is well covered by CI. For running locally, see [All or relevant fraction of full tests run](http://psicode.org/psi4manual/master/build_planning.html#how-to-run-a-subset-of-tests)

## Status
- [x] Ready for review
- Ready for merge -- use Draft/Open GitHub status to signal your view on merge readiness

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5da6bbf05148`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
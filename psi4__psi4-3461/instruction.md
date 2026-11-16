# Issue

**Title:** check add-on running

## Description

## Description
<!-- Provide a brief description of the PR's purpose here. -->

## Dev notes & details
<!-- A bullet-point format description of what this PR does "at a glance."
     Target audience is code reviewers and other devs skimming PRs.
     Should be more technical than user notes. Should never be empty. -->
- [x] When packages are changing and I can't count on a green checkmark on a lane is doing what I intend, it's annoying to go into the logs, remember a relevant test name, and grep it to check PASSED, not SKIPPED. Moreover, comparing what tests are active between CI lanes is difficult.
- [x] So I commissioned of codex a dashboard to show test coverage for the different addons. It shows up on the "Summary" page at the bottom, since there's a collection step to merge the tables.
- [x] These counts are based on `using()` and `uusing()` and doesn't know about `sed read_options.cc` strategems to broaden testing. 
- [x] My goal changed to pretty table, but this also shows how to fail a lane if an addon isn't running and passing tests (e.g., `python -c 'import json; r=json.load(open("addon-report.json"))["addons"]["ecpint"]; assert r["passed"] > 0 and r["failed"] == 0, r'`). Handy sometimes when you don't want psi4 testing to just fail gracefully.

<img width="1153" height="677" alt="Screenshot 2026-08-25 at 6 20 01 PM" src="https://github.com/user-attachments/assets/0dcdb6ff-7c56-4345-871f-1ddd556c2ea7" />

## AI
<!-- Briefly describe where AI contributed to the PR (tests, derivation,
     bug-seeking, code generation, docs, etc.). No restrictions, but a
     person should be submitting the PR and (as usual) be ready to answer
     questions about it. -->
- [x] AI usage -- Codex Sol 5.6 almost entirely

## Status
- [x] Ready for review
- Ready for merge -- use Draft/Open GitHub status to signal your view on merge readiness

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1e5d928bd398`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
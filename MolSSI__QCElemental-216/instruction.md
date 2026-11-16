# Issue

**Title:** codata 2018, round 3

## Description

<!-- Thank you for your contribution! -->

## Description
This fixes the `conversion_factor` problem #215, so I wanted to get it posted. I want to actually rework the tests next. I could have fixed it by accessing the context with `.get()` or `.pc` instead of repeating the 2018/2014 alias, but I figured there was a good reason you were working from `.raw_codata` for the Pint registration.

## Changelog description
- [x] Fixes bug where `conversion_factor` errored on CODATA 2018 context.
- [x] Tests the 2014, 2018, and default contexts in test_constants.py. Toggle a line, then the tests are ready for qcel codata2018 default update.
- [x] Tests the 2014, 2018, and default contexts in conversion_factor. Toggle a line, then the tests are ready for qcel codata2018 default update.
- [x] Right now the bohr->miles 2018 can't be made to work for the inverse conversion. Need to adj `rel_tol` to `+ 0`?
- [x] Adapt the tests to 2018 default *except for hash_canary*

## Status
<!-- Please `pip install .[lint]; make format` in the base folder. -->
- [x] Code base linted
- [x] Ready to go SQUASH!

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a91fd69e1594`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
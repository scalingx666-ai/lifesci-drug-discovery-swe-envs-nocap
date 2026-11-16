# Issue

**Title:** Replace gunicorn with waitress and fix logging issues

## Description

<!-- Thank you for your contribution! -->

## Description
This PR replaces the embedded gunicorn instance with waitress https://docs.pylonsproject.org/projects/waitress/en/latest/#

Gunicorn was not particularly set up to be run in this way. It's largely meant to be used from the command line rather than embedded in application. Its `fork`ing model just didn't well in qcfractal and it conflicted with other multiprocessing stuff. Also, logging was a pain.

So let's try waitress instead. It is much simpler, and much more amenable to embedding in a python application.
I hope this also fixes the spurious `502 Bad Gateway` errors, although I wouldn't be surprised if it doesn't.

Waitress only works with one process, so the `num_workers` parameter in the config is no longer used.

Also as part of this PR, logging will work through a queue. This will help in the multi-process environment, and allow for using TimedRotatingFileHandler and handlers from python.

Lastly, this also quiets some logging when doing admin stuff from the CLI (like modifying users). It enables using `-v` and `-vv`
to increase verbosity

## Changelog description
Replace gunicorn with waitress and fix logging issues
Allow increasing verbosity on the CLI with  `-v` and `-vv` on the cli

## Status
- [x] Code base linted
- [x] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a87767a070d9`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
# Issue

**Title:** Fix doc references

## Description

This PR fixes incorrect doc references and makes some general changes to how we check our internal links.

# The issue

The core issue that is fixed here is that we previously ignored all links that do not contain or start with `baybe`. As a consequence, internal relative links were being skipped, and if those links were broken, we simply didn't know. 

# The fix
We now also check links that do not start with or contain the string `baybe`. This is done by removing the very general regex that we had on top of `conf.py`. As a consequence, we however now need to manually add a lot of additional regexes that we need to ignore now.

# The changes
Some broken internal links were found and are repaired now. 

# Important note
The additional regexes have been identified and added by AI. I did *not* manually review all of them, since "the tests are passing and I checked it manually" is sufficient imo.

# Compiled documentation:

Available at https://avhopp.github.io/baybe_dev/latest/

---

<sub>Stack created with <a href="https://github.com/github/gh-stack">GitHub Stacks CLI</a> • <a href="https://gh.io/stacks-feedback">Give Feedback 💬</a></sub>

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e91d4b8d74d8`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
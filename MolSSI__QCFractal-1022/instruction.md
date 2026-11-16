# Issue

**Title:** Improve JWT Security for disabling/downgrading accounts

## Description

## Description
<!-- Thank you for your contribution! -->
<!-- Provide a brief description of the PR's purpose here. -->

Right now, the server uses the claims (user id, role) present in the JWT without validating against the database. This was by design, as verifying this information for every request (at 10-100/second) starts to add up, but is also nearly 100% unneeded as account info rarely changes.

However, combined with the default JWT access token expiration of 1 hour, this does create a bit of an issue where a disabled user has <=1 hour where the server will still consider them enabled (as long as they have an active JWT). That is too long - I use 5 minutes on the instances I run. This is unlikely to really be a problem at the moment, as users are added manually by a server admin and should be trusted. Nevertheless, it could cause problems in the future if instances have open registration.

So the fix is two fold:

1. Shorten the default in the config file to 15 minutes.
2. Validate the info server side, but use the existing cached validation mechanism, modified to hold for 5 seconds. This will effectively ignore the info in the JWT, although that info is useful to the end user so is kept.

Checking once every 5 seconds is enough that it won't burden the server (could be every 50-1000 requests or so), but short enough that the delay is negligible in an account doing some damage after being disabled.

There should be no user-facing changes.

## Status
- [X] Code base linted
- [X] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d57ba756e7e8`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
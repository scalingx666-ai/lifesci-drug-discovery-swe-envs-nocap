# Issue

**Title:** Use retries for JWT fetching

## Description

## Description
<!-- Thank you for your contribution! -->
<!-- Provide a brief description of the PR's purpose here. -->

We are having a persistent problem with managers being unable to periodically (but frequently) access our server. When the manager client attempts to refresh the JWT, there is a remote disconnect error:

```
('Connection aborted.', RemoteDisconnected('Remote end closed connection without response'))
```

The true cause is still elusive. However, simply retrying on that error seems to be a temporary workaround while I figure out what is going on.

This PR implements retrying for JWT logins and refreshes, similar to other types of requests. In general this would be an ok thing going forward, since you never know when a network might have sporadic issues anywhere.

## Status
- [X] Code base linted
- [X] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `43f985ed8960`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
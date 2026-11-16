# Issue

**Title:** Implement getting direct download url & rework downloads slightly

## Description

## Description
<!-- Thank you for your contribution! -->
<!-- Provide a brief description of the PR's purpose here. -->

This adds the ability to get the direct link of an external file (including dataset attachments and views). To do so, use the `ExternalFile` object. For example, for a dataset attachment or view:

```
a = ds.attachments[0]
a.get_direct_url()
```

Note that URLs coming from an S3 bucket may have an expiration time.

Requested by @chrisiacovella

## Status
- [X] Code base linted
- [X] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `00e296743d14`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
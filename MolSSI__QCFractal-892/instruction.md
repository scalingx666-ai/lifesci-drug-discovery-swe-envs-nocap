# Issue

**Title:** Fix for very large files on S3

## Description

## Description
<!-- Thank you for your contribution! -->
<!-- Provide a brief description of the PR's purpose here. -->

S3 (or boto3?) has a limit of 10,000 parts. I used a part size of 10 MiB, which limits the file size to about 100GiB. We do have datasets that will be bigger than that.

This changes the part size to 256MiB, so a max limit of about 2.56TiB.

(Inside that function, we do not know the end file size, since it is meant to work with BinaryIO streams)

## Status
- [X] Code base linted
- [X] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `65fe9d4150fd`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
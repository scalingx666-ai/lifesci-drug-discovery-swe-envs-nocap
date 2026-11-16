# Issue

**Title:** Update cheminfo dependency to mordredcommunity

## Description

<!--
Thank you for sending the PR! We appreciate you spending the time to make BoFire better.

Help us to understand your motivation by explaining why you decided to make this change.

You can learn more about contributing to BoFire here: https://github.com/experimental-desgin/bofire/blob/main/CONTRIBUTING.md
-->

## Motivation

The `cheminfo` optional dependency uses `mordred`, which is no longer maintained.
This PR changes it to [`mordredcommunity`](https://github.com/JacksonBurns/mordred-community), which is a community-maintained fork of `mordred` with bug fixes and explicit compatibility with your Python versions (3.10+).

### Have you read the [Contributing Guidelines on pull requests](https://github.com/experimental-design/bofire/blob/main/CONTRIBUTING.md#pull-requests)?

:+1:

## Test Plan

`mordredcommunity` is drop-in compatible, even to the level of `import mordred` - the CI should pass without issue

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d3044491ed8d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
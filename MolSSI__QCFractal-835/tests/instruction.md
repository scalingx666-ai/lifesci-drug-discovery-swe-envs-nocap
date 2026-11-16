# Issue

**Title:** Better handling of queue tags (strict queue tags and case insensitivity)

## Description

<!-- Thank you for your contribution! -->

## Description
Some improvement to queue tags

* Fix bug where upper case tags in a manager config are ignored by the server (reported by @hjnpark)
* Add `strict_queue_tags` option. Enabling this option disables the wildcard-pulling behavior of manager ; managers that specify `'*'` as a queue tag will then only pull tasks marked with the `'*'` queue tag (requested by @peastman)

## Changelog description
Better handling of queue tags (strict queue tags and case insensitivity) 

## Status
- [X] Code base linted
- [X] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3e6e5c59cdab`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
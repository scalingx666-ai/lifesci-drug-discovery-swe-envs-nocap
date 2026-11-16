# Issue

**Title:** Replace sqlite3 with apsw

## Description

<!-- Thank you for your contribution! -->

## Description
Replaces the use of sqlite3 from the python standard library with APSW (https://github.com/rogerbinns/apsw, https://rogerbinns.github.io/apsw/index.html)

APSW is a lightweight wrapper around sqlite that allows for more features compared to the python standard library (which is constrained by the DB API).

In particular, APSW allows for multi-threaded access to connections, which means I can remove some kinda hacky thread-local stuff. And since I can remove that, I don't need to use the memdb vfs, which seems constrained in the size of the db (whereas `:memory:` seems unconstrained). So that should prevent things like #820 

It also allows for some more advanced features that I may use in the future.

## Changelog description
Replace use of Python sqlite3 with APSW

## Status
- [X] Code base linted
- [X] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0642482915df`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
# Issue

**Title:** feat: zero downtime deployment for lite version and other improvement…

## Description

…s. (#673)

* feat: zero-downtime deployment for lite version

* feat: enable proxy for Dockerfile.lite and optimize prod-build.yml

* fix: added APT proxy conf

* fix:remove build are for proxy

* fix:remove build arg from prod-build.yml

* fix: pass proxy only from environment variable

* fix: github workflows improvements

* fix: change the docker compose absolute path

* Update .github/workflows/dev-build.yml



---------

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `473c92838e29`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
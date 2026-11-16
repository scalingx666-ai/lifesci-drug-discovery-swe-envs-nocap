# Issue

**Title:** chore(ci): close link-health loop

## Description

Root cause: 13dddc6 cleared 3 of 4 original link-check failures, leaving
www.ensembl.org/ as a persistent 504 (Ensembl bot-blocks HEAD requests
from CI runners; survived 5 lychee retries). Treating external link rot
as an audit signal rather than a build gate avoids future false-red on
flaky academic mirrors.

.lychee.toml: exclude ensembl.org homepage only (deeper paths
  rest.ensembl.org/..., www.ensembl.org/<species>/... stay checked).
check-links: set fail:false on the lychee step + add audit-not-gate
  comment. Weekly schedule (0 9 * * 1) preserved as-is — already weekly,
  no frequency reduction needed.
release.yml, validate-skills.yml: bump actions/checkout v4 -> v5
  (Node 20 deprecation).

Other Node 20 actions still present (separate issue, not auto-bumped):
softprops/action-gh-release@v2 in release.yml.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `13dddc63c48c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
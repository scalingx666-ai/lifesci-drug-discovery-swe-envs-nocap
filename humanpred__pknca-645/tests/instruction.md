# Issue

**Title:** Use cdiscdata 0.2.0's get_ct() directly and install it in CI until it is on CRAN

## Description

cdiscdata 0.2.0 fixes the attach-only bug in get_ct(), so pknca_cdisc_in_ct() now calls cdiscdata::get_ct() directly and the Suggests pin is cdiscdata (>= 0.2.0). The enumerating test drops its copy of the same workaround. Behaviour without cdiscdata installed is unchanged (in_ct stays NA with the same classed message).

cdiscdata is submitted to CRAN but not yet published, which has made main's CI fail in dependency setup since PR 643. The three workflows now install humanpred/cdiscdata from GitHub through pak's extra-packages; no Remotes field is added to DESCRIPTION. The extra entry can be removed once CRAN publishes cdiscdata.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0a76d2bb9ab4`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
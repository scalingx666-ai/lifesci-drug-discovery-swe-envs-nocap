# Issue

**Title:** convey libgcc windows

## Description

## Description
<!-- Provide a brief description of the PR's purpose here. -->
~There's been a strange error message the past few weeks on Windows at runtime that's fixed by `libgcc<14.3`. Let's test the rebuild of g2g 2.0.8 and see if this might have fixed this issue, as g2g was the oldest dep on c-f.~


## User API & Changelog headlines
<!-- A bullet-point format description of how this PR affects the user.
     This is destined for the release notes. May be empty. -->
- [x] conda env spec yaml files including addons are now saved in the repo

## Dev notes & details
<!-- A bullet-point format description of what this PR does "at a glance."
     Target audience is code reviewers and other devs skimming PRs.
     Should be more technical than user notes. Should never be empty. -->
- [x] new adcc version. averts pkg_resources/setuptools restriction
- [x] update reason openfermionpsi4 is blocked (it's fine but restricts the whole conda env to numpy v1)
- [x] now save full conda env with addons yaml files
- [x] convey some windows+conda peculiarities through codedeps rather than GHA sed's
Later
- [x] deployed v1.0.6 Einsums and new conda envs (probably in another PR too)
- [x] v2rdm stopped linking the with "no files found" for Intel Mac. no reason. I just disabled it since on its way out
- [x] the middle (3/4) Linux lane started reliably failing on two of the new GRAC tests with "SVD did not converge" even though it passed them fine three times last week. I added a nan_to_num call b/c there was at least one NaN and lots o e-308 . Austin didn't add that code, just triggered it in a new way. it should be investigated further
- [x] I got rid of the KMP stuff and added lots to detect and coney OpenMP. gauxc is using different (more modern) detection and needs help to see the conda files. If it sees the apt-get omp files, that's when multiple get linked in and triggers the runtime error

## Status
- [x] Ready for review
- [x] Ready for merge

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1d9cb17b579b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
# Issue

**Title:** Prepare 0.9 release

## Description

Previous #101 

Remaining action items:
- [x] Update version [sub]string in all files where it appears in the repository
  - [x] `.mergify.yml`
  - [x] `pyproject.toml`
  - [x] `.github/workflows/docs.yml`
- [x] move release notes to `0.9` directory
- [x] update any remaining `0.9` deprecation warnings from to a later release number
- [x] merge everything except this PR on the milestone
- [x] merge this PR
- [x] build docs locally; proofread the release notes
- [x] tag the release
   1. `git checkout main`
   2. `git pull`
   3. `git show` (verify it's the commit we want to tag)
   4. `git tag -a 0.9.0 -m 0.9.0`
   5. `git show` (double/triple check the tag is on the correct branch)
   6. `git push origin 0.9.0`
- [x] Wait for CI to finish. The release should then be available on GitHub and pypi.
- [x] create the `stable/0.9` branch
   1. start with same commit as above checked out
   2. `git checkout -b stable/0.9`
   3. `git show` (check before pushing)
   4. `git push --set-upstream origin stable/0.9`
- [x] get docs to deploy from the new stable branch (should happen automatically at this point after CI runs both on the new stable branch and then on the `gh-pages` branch)
- [x] move remaining old milestone items to new milestone and close old milestones

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1ee8ddbc625e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
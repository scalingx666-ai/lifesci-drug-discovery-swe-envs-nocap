# Issue

**Title:** Prepare 0.14.0 release

## Description

Previous #341

Remaining action items:
- [x] Update version [sub]string in all files where it appears in the repository
  - [x] `.mergify.yml`
  - [x] `pyproject.toml`
  - [x] `.github/workflows/docs.yml`
- [x] move release notes to `0.13` directory
- [x] merge everything except this PR on the [milestone](https://github.com/Qiskit/qiskit-addon-sqd/milestone/4)
- [x] merge this PR
- [x] build docs locally; proofread the release notes
- [x] tag the release
   1. `git checkout main`
   2. `git pull`
   3. `git show` (verify it's the commit we want to tag)
   4. `git tag -a 0.14.0 -m 0.14.0`
   5. `git show` (double/triple check the tag is on the correct branch)
   6. `git push origin 0.14.0`
- [ ] Wait for CI to finish. The release should then be available on GitHub and pypi.
- [x] create the `stable/0.14` branch
   1. start with same commit as above checked out
   2. `git checkout -b stable/0.14`
   3. `git show` (check before pushing)
   4. `git push --set-upstream origin stable/0.14`
- [ ] get docs to deploy from the new stable branch (should happen automatically at this point after CI runs on the new stable branch)
- [ ] move remaining old milestone items to new milestone and close old milestones
- [ ] update external documentation (e.g. learning platform tutorials, ibm quantum docs)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `86646bf9c189`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
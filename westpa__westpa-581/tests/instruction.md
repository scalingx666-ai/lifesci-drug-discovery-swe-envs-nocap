# Issue

**Title:** Work Manager bug fix/code cleanup (ZMQ-multiprocessing, curbing other wm tests)

## Description

## Issue Number
<!--- Is this pull request related to any outstanding issues? If so, list the issue number. --->


## Describe the changes made
<!--- A clear and concise description of what the problem is and what you did to fix it. E.g. [...] was happening and I've changed [...] to fix it. -->
A copy of the shutdown logic for processes work manager for zmq work manager. This will prevent orphaned processes and unexplained hangs after a run (pytest or simulation). Also defaults to "fork" on UNIX/POSIX on Python 3.14+ to speed things up. Forkserver is slow.

Also refactored the tests for processes and threads so we don't over request the number of workers and that minimize it so the setup only runs once per run.

Also unblocked a few tests that were previously skipped. New test added as well.

## Goals and Outstanding Issues
<!--- A clear and concise list of goals (to be) accomplished. --->
- [x] Better shutdown logic in zeromq to prevent hangs and 
- [x] Run setup for processes and threads tests only once each. 
- [x] Some test clean up

## Major files changed
<!--- Manually list files or include a diff link in the form of: https://github.com/user/westpa/compare/<initial SHA>..<final SHA> --->
- [x] src/westpa/work_managers/zeromq
- [x] tests/test_work_managers/

## Status
<!--- Delete bullet points that are not relevant. --->
- [x] Bug fix (non-breaking change which fixes an issue)
- [ ] New feature (non-breaking change which adds functionality)
- [ ] Breaking change (fix or feature that would cause existing functionality to change)
- [x] I have read the CONTRIBUTING document.
- [x] My code follows the code style of this project.
- [x] My change requires a change to the documentation.
- [x] I have updated the documentation accordingly.
- [x] I have added tests to cover my changes.
- [x] All new and existing tests passed.
- [x] I have read the AI POLICY document.
- [x] This PR conforms to WESTPA's AI policy.
- [x] I have declared all usage of AI in the PR description.

## Additional context
<!--- Add any other context or screenshots about the pull request here. --->

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3a213bbbdec9`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
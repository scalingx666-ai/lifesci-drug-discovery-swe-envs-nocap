# Issue

**Title:** Fix Processes work manager silent hang

## Description

## Issue Number
<!--- Is this pull request related to any outstanding issues? If so, list the issue number. --->
#533 

## Describe the changes made
<!--- A clear and concise description of what the problem is and what you did to fix it. E.g. [...] was happening and I've changed [...] to fix it. -->

Effectively I reorganized the processes manager so during shutdown:
1. Clean up the queues
2. Throw `shutdown_sentinels` to shutdown task_queue
3. throw `shutdown_sentinel` to shutdown result_queue (also modified it so it is no longer blocking, with the default timeout)
4. Send shutdown to the queue retrieval loops via the "shutdown_received" Event
5. Clean queues again
6. Shutdown all workers

- Also fixed the bug where logs (for HDF5 Framework) were not deleted properly.
- Also added functionality for sim_manager to detect whether the work_manager is running (and subsequently shutdown the future-related `self.work_manager.wait_any()`
- safe_extract will use the 'fully_trusted' filter when tarring/untarring. This will unify the behavior between python <3.14 and python >3.14
https://docs.python.org/3/library/tarfile.html#extraction-filters

## Goals and Outstanding Issues
<!--- A clear and concise list of goals (to be) accomplished. --->
- [x] Fix error where existing log dataset leads to hang processes
- [x] Update processes work manager to be more robust

## Major files changed
<!--- Manually list files or include a diff link in the form of: https://github.com/user/westpa/compare/<initial SHA>..<final SHA> --->
- [x] src/westpa/core/h5io.py
- [x] src/westpa/work_managers/processes.py

## Status
<!--- Delete bullet points that are not relevant. --->
- [x] Bug fix (non-breaking change which fixes an issue)
- [x] I have read the CONTRIBUTING document.
- [x] My code follows the code style of this project.
- [x] My change requires a change to the documentation.
- [x] I have updated the documentation accordingly.
- [x] I have added tests to cover my changes.
- [x] All new and existing tests passed.

## Additional context
<!--- Add any other context or screenshots about the pull request here. --->

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `fa7d0a676fb5`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
# Issue

**Title:** Don't kill process when embedded

## Description

This tries is intended as a  fix for 

Using ` exitProcess(0)` will terminate the entire process, but if the kernel is used as a library and embedded in another application, i.e. process this will be terminated too. Instead the code that handles the ShutdownRequest now has a somewhat inelegant check if the kernel is embedded and will instead just throw an `InterruptedException` which is caught in the controlThread loop and leads to the `controlThread` interrupting the `mainThread` so they both terminate and the entire kernel terminates.

Because I don't know why `exitProcess(0)` was used in the first place this will only happen if the kernel is embedded for now, but if this also works for the regular usage this could be simplified to just always throwing an `InterruptedException`

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `dd6d6a58a45b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
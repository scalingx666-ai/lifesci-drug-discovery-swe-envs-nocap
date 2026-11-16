# Issue

**Title:** Fix rich escaping for errors

## Description

Previously missed escaping errors when displaying `redun console`.

The brackets in `[FileNotFoundError]` from the example were not being escaped before being processed by `rich`.

Here is what the fix looks like. Error is probably displayed and `Traceback` header is bold.

<img width="664" alt="Screenshot 2025-05-28 at 7 39 54 PM" src="https://github.com/user-attachments/assets/060fc12b-dcfe-4133-96e7-979737f04818" />

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `733ffb3671c8`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
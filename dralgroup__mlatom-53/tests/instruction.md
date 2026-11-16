# Issue

**Title:** Add timeouts to model-download HTTP requests

## Description

## Summary

Two `requests.get()` calls that download model files run without a `timeout`, so a stalled or unresponsive server hangs the MLatom process indefinitely (no way to recover except killing it):

- `mlatom/model_cls.py:287` — downloading a model from a link (streamed).
- `mlatom/interfaces/torchani_interface.py:1937` — fetching the ANI-1xnr parameters zip from GitHub.

## Fix

Add `timeout=30` to both, consistent with the rest of the codebase, which already sets timeouts on its network calls (`MLatom.py` uses `timeout=3`, `_update_check.py` and `_version.py` use timeouts too).

```diff
- requests.get(link, headers=headers, stream=True, allow_redirects=True)
+ requests.get(link, headers=headers, stream=True, allow_redirects=True, timeout=30)
```
```diff
- resource_res = requests.get(url)
+ resource_res = requests.get(url, timeout=30)
```

Note: requests' `timeout` is a per-read inactivity limit, not a total-duration cap, so this does **not** abort slow-but-progressing streamed downloads — it only unblocks the process when the connection goes dead.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `57f75d2c0482`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
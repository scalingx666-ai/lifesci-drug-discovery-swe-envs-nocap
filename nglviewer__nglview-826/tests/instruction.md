# Issue

**Title:** Sync camera with different view and with itself

## Description

- With other views
```
import nglview as nv

v0 = nv.demo()
v1 = nv.demo()

v0._set_sync_camera([v1])
v1._set_sync_camera([v0])
```

- With itself
```
v0._set_sync_camera([v0]) # v0 here, not v1
```

The sync is done in frontend, there is no roundtrip that causes lagging.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `43846417e4ac`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
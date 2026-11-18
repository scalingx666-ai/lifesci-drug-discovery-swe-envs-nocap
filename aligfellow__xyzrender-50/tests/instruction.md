# Issue

**Title:** Code quality audit: fix bugs, remove redundancies, clean up slop

## Description

- mo.py: Fix type mismatch in classify_mo_lobes (cast to list[bool])
- readers.py: Use lazy logger format for extXYZ debug; log cclib parse exceptions
- renderer.py: Deduplicate ref_scale / _ref_px_per_ang
- api.py: Extract _apply_render_overlays helper; keep cast in _resolve_cmap (ty requires it)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f1f5b36a3006`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
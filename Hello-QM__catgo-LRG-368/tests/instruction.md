# Issue

**Title:** fix(chat): stop CatBot reading a phantom/stale structure

## Description

CatBot's `get_state` read the backend panel store (`/view/structure/current?panel_id=<tab>`) and returned a structure the user couldn't find in any open view (a 580-atom IrO2/TiO2 slab, lattice:null).

**Root cause (two parts):**
1. The MCP bridge reset the backend panel on *start* but never on *cleanup*. When a structure tab closed or became a chat pane, its pushed structure lingered in the backend forever — and CatBot, bound to that `panel_id`, read the ghost.
2. `GET /view/structure/current` fell back to **any** other populated panel when the requested one was empty, so an explicit panel could inherit another panel's stale structure.

**Fixes:**
- **FE** (`tool-handler.ts`): bridge cleanup POSTs `/view/reset?panel_id` so a closed/replaced tab clears its backend structure (mirrors the reset on start).
- **Backend** (`view_capture.py`): only the `"default"` sentinel may borrow another panel's structure; an explicit empty panel returns 404 instead of a phantom. New pytest covers all 3 cases (3 passed).

The live backend's stale panels were also cleared via `/view/reset`. Note: the backend code change takes effect on the next `:8000` restart.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `83ce4dfde46f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
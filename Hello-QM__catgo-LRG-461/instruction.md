# Issue

**Title:** fix(view): SSE events reach tab-alias subscribers after a pane is touched

## Description

## Symptoms (all one root cause)

1. `catgo view <file>` repeatedly: the External tab's **label stays frozen** on the first structure (e.g. 🤖 Fe) while the content does change.
2. `catgo view a.xyz b.poscar c.cif` (multi-file → trajectory): CLI reports "opened trajectory (N frames)" but the viewer **keeps showing the previous structure** — the trajectory never arrives.

## Root cause

SSE subscribers register under the **raw** panel id they request (frontend subscribes to `default`), but writers notify with the **resolved** id: `resolve_panel_id` maps a tab id to its active viewer once `mark_active` has run — i.e. after the user touches any pane. From then on every push to `default` was delivered to a registry key with zero subscribers and vanished.

Why the two symptoms differ: structure pushes have a legacy **poll fallback** in the component (content updated; the App-level SSE injector that refreshes the tab label never fired). Trajectory pushes are **SSE-only** — dropped outright.

## Fix

`_subscriber_keys(panel_id)`: deliver to the resolved key **and** every tab id that currently resolves to it. `_notify` fans out over that set; `has_subscribers` gains the same alias awareness.

## Verification

Direct module test: `subscribe('default')` → `mark_active('default:structure-abc')` → `push_structure` / `push_trajectory` to `default` → subscriber receives both `structure` and `trajectory` events (both dropped before the fix). Live SSE curl previously showed only the connect `snapshot` and no `structure` event for a push — the exact vanishing.

Note: needs a backend restart to take effect (server-side only).

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `55e5d1df08df`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
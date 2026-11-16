# Issue

**Title:** feat(build): nanoparticle / cluster builder (Wulff, octahedron, …)

## Description

## Summary

CatGo had builders for slabs, nanotubes, moiré bilayers and heterostructures — but **nothing for finite nanoparticles / clusters**. This wraps `ase.cluster` and exposes it through **one backend route** shared by three consumers (CLI, in-app pane, MCP tool).

## Shapes
- **wulff** — equilibrium shape from per-facet surface energies (default)
- **octahedron** (length + cutoff), **icosahedron** (shells), **decahedron** (p/q/r)

The cluster is returned as a pymatgen `Structure` centred in a vacuum box, ready for cluster DFT.

## Surfaces
- `models/nanoparticle.py` — `build_nanoparticle(NanoparticleParams)`.
- `POST /api/build/nanoparticle` (`routers/build.py`) — one route, three consumers.
- **CLI**: `catgo nanoparticle --element Au --shape wulff --size 100 -o au.vasp` (`ops.py` + `ops_build.py`).
- **MCP**: `catgo_nanoparticle` tool (`server_claude_code.py` + `mcp_http` dispatch) — builds and pushes to the viewer.
- **Frontend**: new "Nanoparticle" build tab (`NanoparticlePane.svelte` + `api/nanoparticle.ts`), wired into `BuildPane`/`Structure`/`index`; `BuildTab` union updated in both its definitions; en/zh i18n in parity.

## Testing
- Route (in-process + HTTP on :8200): Au wulff size 80 → 79 atoms; Pt icosahedron 3 shells → 55 (magic number); octahedron → 116; decahedron → 192.
- MCP: `catgo_nanoparticle` registered (20 tools), dispatch wired.
- Errors: missing `element` → 400/argparse; surfaces≠energies length → clear error.
- Output is a valid pymatgen `Structure` (Au, 79 sites, 32.2³ vacuum box); `catgo view` renders it.
- `svelte-check`: 0 new errors; en/zh structure keys in parity (19/19).

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `8c9c8077fd4d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
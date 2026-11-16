# Issue

**Title:** feat(cli): `catgo view`/`gui` — open structures/trajectories like ase gui

## Description

## Summary

Adds a standalone viewer entry point that mirrors `ase gui`, reusing the existing `/api/view/upload-and-load` push channel (no new frontend rendering). Closes the gap where `catgo` had no `ase gui`-style "throw a file at a viewer" command.

```
catgo view POSCAR              # single structure (or trajectory if multi-frame)
catgo view */POSCAR            # N single-frame files → one trajectory
catgo view traj.xyz@:10        # per-file frame slice (ase-gui syntax)
catgo view -n -1 a.traj b.traj # global slice: last frame of each
catgo view --interpolate 5 A B # IDPP path between 2 endpoints
catgo view -t -g i,e,fmax OUTCAR -o conv.png   # headless convergence plot
```

## What it does

- **Multi-file → trajectory**: shell-expanded globs stack into one trajectory, one frame per file, natural-sorted (`step_2` before `step_10`).
- **Frame selection (ase gui)**: global `-n/--image-number SLICE` + per-file `filename@SLICE` (number or `START:STOP:STEP`, negatives from end).
- **`--interpolate N`**: insert N frames between 2 endpoints — **IDPP** by default (`--interp-method linear` fallback); ase's idpp.traj/log are contained in a tempdir so cwd stays clean.
- **`-g/--graph` + `-t/--terminal`**: headless per-frame convergence dump/plot (symbols `i,e,epot,ekin,fmax,fave,s,T`; `-o` writes `.png/.pdf` or `.dat/.csv`). The `eval` namespace is **sandboxed** (`__builtins__` emptied) — the formula is the caller's own local CLI arg, but `__import__`/`open` are blocked.
- **No viewer open**: backend auto-starts; the served web UI opens in the browser.

Single whole-file pushes use the server's full parser set; sliced/multi-file paths read via ASE (already a backend dep) and push a combined `.extxyz` the server detects as a trajectory.

## Testing

- `catgo view --help` / `gui` alias; argparse sanity (existing subcommands unaffected).
- glob `step_*/POSCAR` → backend logs `trajectory (~N frames)`; single file → single structure.
- `@:3` / `-n 1:5:2` / `-n -1` frame slices; mixed `POSCAR traj.xyz@-1`.
- IDPP interpolate 5→7 frames, no cwd litter; linear fallback.
- `-t -g i,e,fmax` table; `-o conv.png` plot; data-file output; over-/bad-input errors; eval sandbox blocks `__import__`.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5d87b6771691`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
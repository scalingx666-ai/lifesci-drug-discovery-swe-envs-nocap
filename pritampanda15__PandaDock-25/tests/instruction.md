# Issue

**Title:** GPU CLI: pandadock dock --device and pandadock screen

## Description

Follows #24, which landed the batched search as a library. Nothing could
reach it from the command line: `pandadock dock` takes one ligand, so the
measured gain from filling a device was unavailable to users. These two commits
expose it.

## `pandadock dock --device cpu|cuda|mps`

The handoff is the design. A batched run ends holding DOF vectors; everything
downstream — symmetry-corrected clustering, pose construction, interaction
analysis, files — already exists on the CPU and is what the manuscript
validated. So the batch is converted into exactly the `SearchResult` list
`MonteCarloSearch.run` returns, and nothing below that point can tell which
search produced its input. `--device` changes how poses are found, not what is
done with them.

Energies are recomputed on the CPU in float64 rather than carried across: on MPS
the search runs in float32, and a float32 energy beside a float64 pose would be a
small permanent discrepancy between what a run reports and what its own
coordinates score.

Verified end to end on a 3-torsion ligand — both devices returned 9 clustered
poses through the same output path:

| | time | best |
|---|---|---|
| `--device cpu` | 61.2 s | −7.55 |
| `--device mps --n-chains 256` | 23.3 s | −7.34 |

## `pandadock screen`

Grids are built once per atom signature and reused across the library, and
ligands are bucketed by (torsions, atoms) before packing — everything in a batch
pads to the batch maximum, and size-matched batches measured roughly twice the
throughput of mixed ones. Bucketing sorts rather than exact-matches, since exact
buckets would strand odd sizes in batches of one.

Verified on a ten-ligand library: one batch, 24.6 s, grids served from cache, ten
poses written and readable, each docked into the site with its score attached.

## On the README

The performance section carries two framings deliberately. End to end the device
is 2.6× faster here, which is what a user experiences. Like for like — the same
batched search on CPU versus on the device — a single small ligand is *slower*,
and the gain only appears once several ligands fill it. Quoting only the first
would mislead. The section also states the measurements are from a laptop rather
than a datacentre GPU, and makes no pose-accuracy claim for the GPU path beyond
its agreement with the CPU objective.

The screening docs note that docking scores track ligand size, since a command
that hands back a sorted CSV invites exactly that misreading.

## Checks

- 162 tests pass locally; blocking lint (`E9,F63,F7,F82`) reports 0
- Both commands exercised end to end, outputs verified readable and correctly
  positioned
- CUDA throughput is still uncharacterised — every number above is CPU or MPS

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `547bf3cb3822`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
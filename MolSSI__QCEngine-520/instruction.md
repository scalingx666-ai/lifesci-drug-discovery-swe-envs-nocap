# Issue

**Title:** add Orb universal machine learned force field harness

## Description

## Description

I've added a harness for [orb-models](https://github.com/orbital-materials/orb-models). It is based on the previously implemented AIMNET2 harness. It supports `energy` and `gradient` drivers, same as AIMNET2. Three main things are different from the AIMNET2 implementation.

- **Force output keys differ between orb's two model types.** AIMNET2 only has one mode
  (forces by autograd on the energy). For Orb direct models return a
  `forces` key while conservative models return `grad_forces` since Orb has both direct and conservative models. The harness reads the key name off the model rather than hardcoding it, so both families of models go through the same code path.
- **The omol models need both charge and multiplicity for the input** AIMNET2 passes charge but never needs
  multiplicity whereas Orb's omol models need both charge and spin multiplicity. Orb requires both on `atoms.info` and will throw an error if either is missing.
- **The device is selectable for orb models** AIMNET2 hardcodes cpu but in Orb a `device` keyword chooses cpu/cuda and defaults to cuda when available. The tests pin `"cpu"` so reference values don't depend on the runner.

### Verification

- Tests are the same as AIMNET2 with hardcoded water energies/gradients so a dropped unit conversion or flipped sign fails CI, which was checked by introducing both bugs.
- As a final check I ran geometry optimizations on some caffeine conformers. I generated 4 ETKDG
  starting conformers and ran a geometry optimization with 3 models (orb direct, orb conservative and AIMNET2) and every run converged.

<img width="6023" height="3897" alt="Convergence plot, inset is one of the rendered minima, done using OVITO the marker is the last step above each run's converged energy which is off scale." src="https://github.com/user-attachments/assets/ade0b6dd-f576-476f-b729-b5504692e142" />

*Convergence plot, inset is a render of one of the minima done using OVITO, the marker is the last step above each run's converged energy which is off scale.

## Changelog description

ORB - Added harness for orb-models universal ML interatomic potentials.

## Status

- [x] Code base linted
- [x] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `bf1b799c4a17`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
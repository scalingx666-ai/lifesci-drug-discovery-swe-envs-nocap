# Issue

**Title:** Minor simplification of Diffusion Loss

## Description

Diffusion loss contains `noised_atom_coords` only for the shape. The shape can actually be extracted out of the `denoised_atom_coords` as they are the same shape.

Another potential simplification/modification is to use `resolved_atom_mask` in the weighted_rigid_align
```python
# instead of
atom_coords_aligned_ground_truth = weighted_rigid_align(
    atom_coords.detach(),
    denoised_atom_coords.detach(),
    align_weights.detach(),
    mask=feats["atom_resolved_mask"]
    .float()
    .repeat_interleave(multiplicity, 0)
    .detach(),
)

# we can do
atom_coords_aligned_ground_truth = weighted_rigid_align(
    atom_coords.detach(),
    denoised_atom_coords.detach(),
    align_weights.detach(),
    mask=resolved_atom_mask.detach(),
)
```
I haven't made this change because there is a chance that we do not want the `filter_by_plddt` to modify this. Would be happy to also add this.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `bb221d396506`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
# Issue

**Title:** Fix Simpson quadrature for uniform points

## Description

## Background (can be ignored)
@abussy noted a difference between DFTK and QE in the way the hankel transform is computed for the psps, leading to differences in the total energy. This is particularly noticeable for the iron psp from PseudoDojo.

The beta projectors have coefficients on a uniform radial grid, all of them being zero after some point, which is reported in the UPF file. For the `PP_BETA.6` entry of `Fe_pd_nc_sr_pbe_standard_0.4.1.upf`, the metadata says:
```
<PP_BETA.6
size="1426"
...
cutoff_radius_index=" 160"
...
```
which means that there are 1426 entries, but only the first 160 are nonzero.

For this file, DFTK only considers the first 160 entries, whereas QE apparently considers entry up to its radial cutoff, i.e. about 1000 entries. This in turn leads to a small difference in the integral value. It could be compensated by making DFTK assume 0 padding on the right, but I'm not convinced that we need to mimic QE behavior here. Part of the problem also comes from the tabulated beta projector not being super "smooth" in its last few values, which is why this difference matters in the first place, as can be seen in this rough plot of the corresponding `r2_projs` entries:
![image](https://github.com/user-attachments/assets/c8af75a0-1e36-4bb7-861e-5475d8a8e657)

## Actual changes
In any case, I propose these two changes:
1. The `isodd(n_intervals) ? n - 1 : n - 2` check was flipped, as noticed by @abussy. This means that the easy case with an odd number of points was accidentally wrong!!
2. I changed the handling of the last interval from a trapezoidal rule to a higher order formula, to ensure that we achieve overall degree of exactness 2. This also makes the uniform rule consistent with the nonuniform rule below. We could aim for degree of exactness 3 but I don't think it's worth it - the method is still 4th order in spite of that.

Overall, the Simpson rule implemented in DFTK now has degree of exactness 2 (actually 3 for odd uniform points), and this is verified in a test.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a4543a20afe6`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
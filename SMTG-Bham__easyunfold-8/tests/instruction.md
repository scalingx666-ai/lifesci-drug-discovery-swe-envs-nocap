# Issue

**Title:** Allow customized terminal color for projected spectral function

## Description

This is the final bits of code needed to allow custom colours to be used when generating projected plots. 

Supersedes #4 

Allow any terminal colours to used via interpolation in a specific colour space (default to RGB).   

Example output (MgO supercell example with projection):

```
easyunfold unfold  plot-projections --atoms-idx="1,2,3,4|5,6,7,8" --procar MgO_super/PROCAR  --emin="-5" --emax=15 --intensity=2  --combined --colors="r,b" --out-file unfold-proj.png
```

![image](https://user-images.githubusercontent.com/33688599/218322114-fb472cdd-5559-446a-9fa0-156e5bbdbbea.png)

```
easyunfold unfold  plot-projections --atoms-idx="1,2,3,4|5,6,7,8" --procar MgO_super/PROCAR  --emin="-5" --emax=15 --intensity=2  --combined --colors="xkcd:baby poop,xkcd:berry" --out-file unfold-proj.png
```

![image](https://user-images.githubusercontent.com/33688599/218322232-f0397ff9-f900-493b-823f-d5e617c83265.png)


A potential pitfall is that when there are multiple species, the colours may mix and become white. However, as long as the projections are well separated along the energy/kdistance axis. This should not be a problem.

The other issue is that the use of `imshow` means that it is not possible to have the xaxis in the scale consistent with the actual kpoint distance. This is because the sampled kpoints along the path may not take equal distances in each segment. 
The `pyplot.pcolormesh` solves this (as in the standard spectral function plot), but getting it to display colors from RGB(A) arrays requires calling directly the `matplotlib.collections.QuadMesh` constructor and supply colours, but it is difficult to have the colors in the right order it seems.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0dada89070cb`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
# Issue

**Title:** Read Arbitrary Per-Atom Properties in LAMMPS Atoms Format

## Description

Read per-atom properties (see discussion in #409). LAMMPS cannot store any frame properties, so nothing to do here. Also, all LAMMPS fixes, computes, or variables are either integer or double. Reading string properties is only a fallback if something went wrong, e.g. when dealing with incorrect user-generated data or upstream changes in LAMMPS.
Array data is written element-wise which means that a 3D property results in 3 scalar properties `myProp[I]` where `I = 1, 2, 3`.

Edit: Tests failing due to changes in #412. Waiting for these changes to be merged and then run tests again.
<details>
<summary>How to generate test input</summary>

```
variable x index 1
variable y index 1
variable z index 1
variable   t index 300

variable xx equal 10*$x
variable yy equal 10*$y
variable zz equal 10*$z

units         lj
atom_style    atomic

lattice       fcc 1.5
region        box block 0 ${xx} 0 ${yy} 0 ${zz}
create_box    1 box
create_atoms  1 box
mass     1 1.0

velocity all create 1.44 87287 loop geom

pair_style    lj/cut 2.5
pair_coeff    1 1 1.0 1.0 2.5

neighbor 0.3 bin
neigh_modify  delay 0 every 20 check no

fix      1 all nve

compute stress all stress/atom NULL
variable sq_pos atom "x^2+y^2+z^2"
fix 2 all property/atom i_flag

variable cluster atom (id%2)
set atom * i_flag v_cluster

dump 3 all custom 100 lj_dump.lammpstrj id type x y z c_stress[*] v_sq_pos i_flag
#dump 4 all netcdf 100 lj_dump.nc x y z c_stress[*]

#compute 6 all property/local ntype1 ntype2
#dump 5 all local 100 local.txt index c_6[1]

run      $t
```
</details>

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d709895c924b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
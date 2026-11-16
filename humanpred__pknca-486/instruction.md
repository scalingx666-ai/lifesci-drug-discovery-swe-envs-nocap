# Issue

**Title:** Added New AUC Pk Parameters

## Description

1. Clearance (CL)
Description: Calculate oral or IV clearance.
Function name: pk.calc.cl
•	Existing parameters:
cl.last, cl.all, cl.obs, cl.pred
•	New parameters added:
cl.int.all, cl.int.inf.obs, cl.int.inf.pred, cl.int.last, cl.iv.all, cl.iv.last, cl.iv.obs, cl.iv.pred,
cl.ivint.all, cl.ivint.last,
cl.sparse.last
________________________________________
3. Elimination Rate Constant (Kel) Description: Calculate the elimination rate constant (Kel). Function name: pk.calc.kel
•	Existing parameters:
kel.last, kel.obs, kel.pred,
kel.iv.last, kel.iv.obs, kel.iv.pred
•	New parameters added:
kel.all, kel.int.all, kel.int.inf.obs, kel.int.inf.pred, kel.int.last, kel.iv.all,
kel.ivint.all, kel.ivint.last,
kel.sparse.last
________________________________________
4. Mean Residence Time (MRT) — Oral or General Description: Calculate the mean residence time (MRT) for single-dose or linear multiple-dose data. Function name: pk.calc.mrt
•	Existing parameters:
mrt.last, mrt.obs, mrt.pred
•	New parameters added:
mrt.all, mrt.int.all, mrt.int.inf.obs, mrt.int.inf.pred, mrt.int.last, mrt.sparse.last
________________________________________
5. Mean Residence Time (MRT) — IV Infusion Description: MRT calculation specifically for IV infusion. Function name: pk.calc.mrt.iv
•	Existing parameters:
mrt.iv.last, mrt.iv.obs, mrt.iv.pred
•	New parameters added:
mrt.iv.all,
mrt.ivint.all, mrt.ivint.last
________________________________________
6. Steady-State Volume of Distribution (Vss) Description: Calculate the steady-state volume of distribution (Vss). Function name: pk.calc.vss
•	Existing parameters:
vss.iv.last, vss.iv.obs, vss.iv.pred,
vss.last,
vss.md.obs, vss.md.pred,
vss.obs, vss.pred
•	New parameters added:
vss.all, vss.int.all, vss.int.inf.obs, vss.int.inf.pred, vss.int.last, vss.iv.all,
vss.ivint.all, vss.ivint.last,
vss.sparse.last
________________________________________
7. Terminal Volume of Distribution (Vz) Description: Calculate the terminal volume of distribution (Vz). Function name: pk.calc.vz
•	Existing parameters:
vz.obs, vz.pred
•	New parameters added:
vz.all, vz.int.all, vz.int.inf.obs, vz.int.inf.pred, vz.int.last, vz.iv.all, vz.iv.last, vz.iv.obs, vz.iv.pred,
vz.ivint.all, vz.ivint.last,
vz.last; vz.sparse.last

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e2413229945c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
# Issue

**Title:** Print atomic dispersion energies

## Description

- print atomic dispersion energies in Hartree and kcal/mol
- requires additional verbosity level (i.e., >2)

<details>
<summary>Example Output</summary>

```
-----------------------------------
 s i m p l e   D F T - D 3  v1.0.0
-----------------------------------

Rational (Becke-Johnson) damping: D3(BJ)
---------------------
  s6         1.0000
  s8         2.4000
  s9         0.0000
  a1         0.6300
  a2         5.0000
 alp        14.0000
--------------------

Atom-resolved dispersion energies:
--------------------------------------------------
     #    Z           [Hartree]      [kcal/mol]
--------------------------------------------------
     1   11 Na  -0.76748306E-03     -0.48160289
     2    1 H   -0.24893380E-03     -0.15620832
     3    8 O   -0.36382575E-03     -0.22830411
     4    1 H   -0.28480067E-03     -0.17871512
     5    9 F   -0.30407223E-03     -0.19080820
     6    1 H   -0.30221975E-03     -0.18964576
     7    1 H   -0.35383148E-03     -0.22203261
     8    8 O   -0.43647474E-03     -0.27389203
     9    7 N   -0.66531601E-03     -0.41749210
    10    1 H   -0.24273005E-03     -0.15231541
    11    1 H   -0.28733317E-03     -0.18030428
    12   17 Cl  -0.97017183E-03     -0.60879201
    13    5 B   -0.57848073E-03     -0.36300214
    14    5 B   -0.57521461E-03     -0.36095262
    15    7 N   -0.59906392E-03     -0.37591828
    16   13 Al  -0.10276807E-02     -0.64487938
--------------------------------------------------

Dispersion energy:      -8.0076324944923E-03 Eh

[Info] Dispersion energy written to .EDISP

```
</details>

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5ee8c4d71414`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
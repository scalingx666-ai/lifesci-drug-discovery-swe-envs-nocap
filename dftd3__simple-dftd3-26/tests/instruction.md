# Issue

**Title:** Add parameters for B97-3c

## Description

The parameters are taken from doi: 10.1063/1.5012601. To verify my implementation, I compare the results of s-dftd3 and ORCA, with a molecule `N 0.0 0.0 0.0; N 0.0 0.0 1.1; N 0.0 0.0 3.0; N 0.0 0.0 4.1`

`s-dftd3 --bj b973c --atm test.xyz` gives
```
Rational (Becke-Johnson) damping: b973c-D3(BJ)-ATM
---------------------
  s6         1.0000
  s8         1.5000
  s9         1.0000
  a1         0.3700
  a2         4.1000
 alp        14.0000
--------------------

Dispersion energy:      -4.4671172794224E-03 Eh
```
while ORCA 5.0.3 gives
```

                              DFTD3 V3.1  Rev 1
                          USING Becke-Johnson damping
-------------------------------------------------------------------------------
The B97-3c composite method is recognized
Using three-body term ABC
Active option DFTDOPT                   ...         4

molecular C6(AA) [au] = 344.619512


            DFT-D V3
 parameters
 s6 scaling factor         :     1.0000
 a1 scaling factor         :     0.3700
 s8 scaling factor         :     1.5000
 a2 scaling factor         :     4.1000
 Damping factor alpha9(ATM):    16.0000
 ad hoc parameters k1-k3   :    16.0000     1.3333    -4.0000

 Edisp/kcal,au: -2.803158856868  -0.004467117508
 E6   /kcal   :  -1.422026801
 E8   /kcal   :  -1.380992171
 E6(ABC)      :  -0.000139885
 % E8         :  49.265569348
 % E6(ABC)    :   0.004990275

-------------------------   ----------------
Dispersion correction           -0.004467118
```
The D3 energies agree well but it seems ORCA adopt a different ATM parameter. Is that a known discrepancy?

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `84ba953a5e25`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
# Issue

**Title:** Fix initial Trial MTD timestep determination

## Description

Proposed bugfix for issue #452. MTDs will now properly run when timesteps are decreased in the rescue protocol.

Primary issue seemed to be that `env%calc` was not reset between trial MTDs.

```
 -----------------------------------
 Starting trial MTD to test settings
 -----------------------------------

> Molecular dynamics settings
 MD time /ps        :      1.00
 dt /fs             :      5.00
 temperature /K     :    300.00
 max steps          :       200
 block length (av.) :      1000
 dumpstep(trj) /fs  :     20.00     4
 # deg. of freedom  :        26
 thermostat         : berendsen
 SHAKE constraint   :        T
 # SHAKE bonds      :        10 (all bonds)
 hydrogen mass /u   :   2.00000
>--- metadynamics parameter ---
 MTD/CV type   : RMSD bias
 kpush /Eh     :    0.0360
 alpha /bohr⁻² :    0.5000
 ramp          :    0.0300 331
 dump/fs       :  550.0000 110
 # CVs (max)   :         1

> Starting simulation

           time (ps)       <Epot>        Ekin     <T>       T            Etot
      1      0.01       -23.79718      0.0278     0.0     0.0       -23.76939

 average properties
 ----------------------
 <Epot> / Eh          :  -23.291204758120546
 <Ekin> / Eh          :   1.0029948329679817E-002
 <Etot> / Eh          :  -23.281174809790869
 <T> / K              :   243.63155137495016
 MD terminated, but still taking as converged.
 Trial MTD 1 did not converge!
 Reducing the time step to  4.0 fs and trying again ...


> Molecular dynamics settings
 MD time /ps        :      1.00
 dt /fs             :      4.00
 temperature /K     :    300.00
 max steps          :       250
 block length (av.) :      1250
 dumpstep(trj) /fs  :     20.00     5
 # deg. of freedom  :        26
 thermostat         : berendsen
 SHAKE constraint   :        T
 # SHAKE bonds      :        10 (all bonds)
 hydrogen mass /u   :   2.00000
>--- metadynamics parameter ---
 MTD/CV type   : RMSD bias
 kpush /Eh     :    0.0360
 alpha /bohr⁻² :    0.5000
 ramp          :    0.0300 331
 dump/fs       :  550.0000 138
 # CVs (max)   :         1

> Starting simulation

           time (ps)       <Epot>        Ekin     <T>       T            Etot
      1      0.00       -23.79718      0.0278     0.0     0.0       -23.76939
  adding snapshot to metadynamics bias, now at 1 CVs
    200      0.80       -23.78344      0.0193   238.8   468.0       -23.74922

 average properties
 ----------------------
 <Epot> / Eh          :  -23.687369386396103
 <Ekin> / Eh          :   1.2116158455813273E-002
 <Etot> / Eh          :  -23.675253227940289
 <T> / K              :   294.30644947188284
 normal MD termination
 Trial MTD 2 runtime (1.0 ps) ...        0 min,  1.227 sec
 Estimated runtime for one MTD (5.0 ps) on a single thread: 6 sec
 Estimated runtime for a batch of 14 MTDs on 8 threads: 12 sec
 ********************************************************************************
**                    N E W   I T E R A T I O N  C Y C L E                    **
********************************************************************************

 ------------------------------
 Meta-Dynamics Iteration 1
 ------------------------------
 list of applied metadynamics Vbias parameters:
$metadyn    0.03600   1.300
$metadyn    0.01800   1.300
$metadyn    0.00900   1.300
$metadyn    0.03600   0.780
$metadyn    0.01800   0.780
$metadyn    0.00900   0.780
$metadyn    0.03600   0.468
$metadyn    0.01800   0.468
$metadyn    0.00900   0.468
$metadyn    0.03600   0.281
$metadyn    0.01800   0.281
$metadyn    0.00900   0.281
$metadyn    0.01200   0.100
$metadyn    0.06000   0.800

  ::::::::::::: starting MTD    1 :::::::::::::
  |   MD simulation time   :     5.0 ps       |
  |   target T             :   300.0 K        |
  |   timestep dt          :     4.0 fs       |
  |   dump interval(trj)   :   100.0 fs       |
  |   SHAKE algorithm      : true (all bonds) |
  |   dump interval(Vbias) :    1.00 ps       |
  |   Vbias prefactor (k)  :  0.0360 Eh       |
  |   Vbias exponent (α)   :  1.3000 bohr⁻²   |
  ::::::::::::: starting MTD    5 :::::::::::::
  |   MD simulation time   :     5.0 ps       |
  |   target T             :   300.0 K        |
  |   timestep dt          :     4.0 fs       |
  |   dump interval(trj)   :   100.0 fs       |
  |   SHAKE algorithm      : true (all bonds) |
  |   dump interval(Vbias) :    1.00 ps       |
  |   Vbias prefactor (k)  :  0.0180 Eh       |
  |   Vbias exponent (α)   :  0.7800 bohr⁻²   |
  ::::::::::::: starting MTD    3 :::::::::::::
  |   MD simulation time   :     5.0 ps       |
  |   target T             :   300.0 K        |
  |   timestep dt          :     4.0 fs       |
  |   dump interval(trj)   :   100.0 fs       |
  |   SHAKE algorithm      : true (all bonds) |
  |   dump interval(Vbias) :    1.00 ps       |
  |   Vbias prefactor (k)  :  0.0090 Eh       |
  |   Vbias exponent (α)   :  1.3000 bohr⁻²   |

...

```

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c39758df941e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
# Issue

**Title:** Return NA rather than 0 when a summed input is zero-length

## Description

.

sum() of a zero-length vector is 0, so five calculation functions returned a plausible number where the answer was unknown.  A clearance of 0 is not a missing value; it summarizes, plots, and exports like any other result.

  pk.calc.cl(dose = numeric(0), auc = 10)              was 0, now NA
  pk.calc.totdose(dose = numeric(0))                   was 0, now NA
  pk.calc.ae(conc = numeric(0), volume = numeric(0))   was 0, now NA
  pk.calc.clr(ae = numeric(0), auc = 10)               was 0, now NA
  pk.calc.fe(ae = numeric(0), dose = 100)              was 0, now NA

NA inputs already behaved correctly, which is what made the zero-length case easy to miss.

pk.calc.count_conc() and pk.calc.count_conc_measured() are unchanged: 0 is the documented answer for no measurements, and a test now pins that so the distinction is not lost.  pk.calc.c0.method.set0() is likewise unchanged, as it returns 0 by definition.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `33f8925075a0`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
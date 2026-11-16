# Issue

**Title:** RDKit atropisomers

## Description

RDKit support atropisomer from SMILES using a custom extension and abusing wedges in CXSMILES where there no coordinates. I'm not a massive fan of this approach but I don't have anything better and so Roger convinced me to add support. 

You can therefore now depict and test CIP rules on atropisomers in CDK depict.

Some examples from Roger:

```
Cc1c(C)c(C)c(-c2c(C)c(C)c(C)c(C)c2Br)c(Br)c1C |wU:6.5|  ABEFET
Oc1ccc2ccccc2c1-c1c(O)ccc2ccccc12 |wU:10.10|    (S)-(−)-1,1′-Bi(2-napthol)
Oc1ccc2ccccc2c1-c1c(O)ccc2ccccc12 |wU:10.11|    (R)-(+)-1,1'-Bi(2-napthol)
Oc1ccc2ccccc2c1-c1c(O)ccc2ccccc12 |wU:10.10|    (S)-BINOL
Oc1ccc2ccccc2c1-c1c(O)ccc2ccccc12 |wU:10.11|    (R)-BINOL
O=C(O)CSc1nnc(Br)n1-c1ccc(C2CC2)c2ccccc12 |wU:10.10|    TIPQER01
O=C(O)CSc1nnc(Br)n1-c1ccc(C2CC2)c2ccccc12 |wU:10.9|     TIPQER03
O=C(O)CSc1nnc(Br)n1-c1ccc(C2CC2)c2ccccc12 |wU:10.9|     (+)-lesinurad
O=C(O)CSc1nnc(Br)n1-c1ccc(C2CC2)c2ccccc12 |wU:10.10|    (-)-lesinurad
C=CC(=O)N1CCN(c2nc(=O)n(-c3c(C)ccnc3C(C)C)c3nc(-c4c(O)cccc4F)c(F)cc23)[C@@H](C)C1 |wU:12.23|    (m)-sotorasib
C=CC(=O)N1CCN(c2nc(=O)n(-c3c(C)ccnc3C(C)C)c3nc(-c4c(O)cccc4F)c(F)cc23)[C@@H](C)C1 |wU:12.11|    (p)-sotorasib
Cc1c(-c2c(-c3ccc(F)o3)sc3ncnc(O[C@H](Cc4ccccc4OCc4ccnn4CC(F)(F)F)C(=O)O)c23)ccc(OCCN2CCN(C)CC2)c1Cl |wU:17.18|  S-63845
```

![](https://www.simolecule.com/cdkdepict/depict/bot/svg?smi=Oc1ccc2ccccc2c1-c1c(O)ccc2ccccc12%20%7CwU%3A10.10%7C%20%20%20%20(S)-(%E2%88%92)-1%2C1%E2%80%B2-Bi(2-napthol)&w=-1&h=-1&abbr=on&hdisp=S&zoom=1.3&annotate=cip&r=0)
![](https://www.simolecule.com/cdkdepict/depict/bot/svg?smi=Oc1ccc2ccccc2c1-c1c(O)ccc2ccccc12%20%7CwU%3A10.11%7C%20%20%20%20(R)-(%2B)-1%2C1%27-Bi(2-napthol)&w=-1&h=-1&abbr=on&hdisp=S&zoom=1.3&annotate=cip&r=0)
![](https://www.simolecule.com/cdkdepict/depict/bot/svg?smi=C%3DCC(%3DO)N1CCN(c2nc(%3DO)n(-c3c(C)ccnc3C(C)C)c3nc(-c4c(O)cccc4F)c(F)cc23)%5BC%40%40H%5D(C)C1%20%7CwU%3A12.23%7C%20%20%20%20(m)-sotorasib&w=-1&h=-1&abbr=on&hdisp=S&zoom=1.3&annotate=cip&r=0)
![](https://www.simolecule.com/cdkdepict/depict/bot/svg?smi=C%3DCC(%3DO)N1CCN(c2nc(%3DO)n(-c3c(C)ccnc3C(C)C)c3nc(-c4c(O)cccc4F)c(F)cc23)%5BC%40%40H%5D(C)C1%20%7CwU%3A12.11%7C%20%20%20%20(p)-sotorasib&w=-1&h=-1&abbr=on&hdisp=S&zoom=1.3&annotate=cip&r=0)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `441d1832449a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
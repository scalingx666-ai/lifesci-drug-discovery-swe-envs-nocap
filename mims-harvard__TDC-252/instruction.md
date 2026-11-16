# Issue

**Title:** add gene perturb outcome tasks

## Description

here is an initial PR for adding scperturb datasets - here are the demo code:

```
from tdc.multi_pred import PerturbOutcome
test_loader = PerturbOutcome(name="scperturb_gene_NormanWeissman2019")
testdf = test_loader.get_data()
```

here are the dataset supported "scperturb_gene_NormanWeissman2019"/  "scperturb_gene_ReplogleWeissman2022_rpe1"/ "scperturb_gene_ReplogleWeissman2022_k562_essential"
 
 this also supports the existing drug perturbation datasets

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0469d9af0d41`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
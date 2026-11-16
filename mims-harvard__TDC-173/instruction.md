# Issue

**Title:** Add pampa_ncats dataset

## Description

Pull request for #172

[Script for data download and basic preprocessing](https://gist.github.com/iwwwish/86b2d832405d8cd3a70fece5badad903)

### PAMPA Permeability

**Dataset Description**: PAMPA (parallel artificial membrane permeability assay) is a commonly employed assay to evaluate drug permeability across the cellular membrane. PAMPA is a non-cell-based, low-cost and high-throughput alternative to cellular models. Although PAMPA does not model active and efflux transporters, it still provides permeability values that are useful for absorption prediction because the majority of drugs are absorbed by passive diffusion through the membrane.

**Task Description**: Binary classification. Given a compound's SMILES string, predict whether it is has high permeability (1) or low-to-moderate permeability (0) in PAMPA assay.

**Dataset Statistics**: NCATS set - 2035 compounds; Approved drugs set - 142 drugs.

**Dataset Split**: `Random Split` `Scaffold Split`

```python
from tdc.single_pred import ADME
data = ADME(name = 'pampa_ncats') # validation_set = False by default
data, validation_set = ADME(name = 'pampa_ncats', validation_set = True)
split = data.get_split()
```

**Reference**: Siramshetty, V.B., Shah, P., et al. "Validating ADME QSAR Models Using Marketed Drugs." SLAS Discovery 2021 Dec;26(10):1326-1336. doi: 10.1177/24725552211017520.

**Dataset License**: Not Specified. CC BY 4.0.

**Updated Dataverse Metadata IDs**: NCATS set - [6576972](https://dataverse.harvard.edu/api/access/datafile/6576972); Approved drugs set - [6576980](https://dataverse.harvard.edu/api/access/datafile/6576980)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `aa179eda91be`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
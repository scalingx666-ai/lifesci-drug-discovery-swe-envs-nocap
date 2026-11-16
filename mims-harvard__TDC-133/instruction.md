# Issue

**Title:** Add herg_central data set

## Description

Pull request for 

[Data download and processing script](https://gist.github.com/benb111/1de21f429a55c0816bc096e48c9dbd21)

### hERG Central

**Dataset Description:** Human ether-à-go-go related gene (hERG) is crucial for the coordination of the heart's beating. Thus, if a drug blocks the hERG, it could lead to severe adverse effects. Therefore, reliable prediction of hERG liability in the early stages of drug design is quite important to reduce the risk of cardiotoxicity-related attritions in the later development stages. There are three targets: `hERG_at_1uM`, `hERG_at_10uM`, and `hERG_inhib`.

**Task Description:**
* `hERG_at_1uM`: Regression. Given a drug SMILES string, predict the percent inhibition at a 1µM concentration.
* `hERG_at_10uM`: Regression. Given a drug SMILES string, predict the percent inhibition at a 10µM concentration.
* `hERG_inhib`: Binary classification. Given a drug SMILES string, predict whether it blocks (1) or not blocks (0). This is equivalent to whether `hERG_at_10uM < -50`, i.e. whether the compound has an IC50 of less than 10µM.

**Dataset Statistics:** 306,893 drugs.

**Dataset Split:** `Random Split` `Scaffold Split`

**Note:** herg_central contains multiple assays data. To retrieve the specific labels for that assay, specify the label name in the `label_name` variable to the data loader. You can find all available label names by calling:

```
from tdc.utils import retrieve_label_name_list
label_list = retrieve_label_name_list('herg_central')
```

Then, go to the standard TDC data loader procedure with the label name specified.

```
from tdc.single_pred import Tox
data = Tox(name = 'herg_central', label_name = label_list[0])
split = data.get_split()
```

**References:**

[1]  Du F, Yu H, Zou B, Babcock J, Long S, Li M. hERGCentral: a large database to store, retrieve, and analyze compound-human Ether-à-go-go related gene channel interactions to facilitate cardiotoxicity assessment in drug development. Assay Drug Dev Technol. 2011 Dec;9(6):580-8. doi: 10.1089/adt.2011.0425.

**Dataset License:** Not Specified. CC BY 4.0.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e401f3391769`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
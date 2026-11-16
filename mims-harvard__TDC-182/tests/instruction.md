# Issue

**Title:** [add] add herg_karim dataset

## Description

- Data processing scripts
```
import pandas as pd
train_val_fn = "Karim_CardioTox_Table2/train_validation_cardio_tox_data.csv"
test1_fn = "Karim_CardioTox_Table2/external_test_set_pos.csv"
test2_fn = "Karim_CardioTox_Table2/external_test_set_neg.csv"
test3_fn = "Karim_CardioTox_Table2/external_test_set_new.csv"
train_df = pd.read_csv(train_val_fn)
test1_df =pd.read_csv(test1_fn)
test2_df =pd.read_csv(test2_fn)
test3_df =pd.read_csv(test3_fn)

total_df = pd.concat([train_df, test1_df,test2_df,test3_df], ignore_index=True)
total_df['Drug_ID']=list(range(len(total_df)))
total_df =total_df.rename(columns={'smiles': 'Drug', 'ACTIVITY': 'Y'})
total_df.to_csv("herg_karim.csv", columns=["Drug_ID", "Drug", "Y"],index=False)
```

- Dataset description
A integrated Ether-a-go-go-related gene (hERG) dataset consisting of molecular structures labelled as hERG (<10uM) and non-hERG (>=10uM) blockers in the form of SMILES strings was obtained from the DeepHIT, the BindingDB database, ChEMBL bioactivity database, and other literature.

- Task description
Binary classification. Given a drug SMILES string, predict whether it blocks (1, <10uM)  or not blocks (0, >=10uM).

- Dataset Statistics
Total: 13445; Train_val: 12620; Test: 825

- Dataset Split: Custom split
```
from tdc.single_pred import Tox
data = Tox(name = 'herg_karim')
train, test = data[:12620], data[12620:]
```
- References:
[1] Karim, A., et al. CardioTox net: a robust predictor for hERG channel blockade based on deep learning meta-feature ensembles. J Cheminform 13, 60 (2021). https://doi.org/10.1186/s13321-021-00541-z

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `4aecc1733fef`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
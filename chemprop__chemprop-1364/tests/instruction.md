# Issue

**Title:** Add general callbacks to `predict` subcommand; Add explanations with Myerson values

## Description

## Description
- This PR adds the option to add a custom [PyTorch Lightning Callback](https://lightning.ai/docs/pytorch/stable/extensions/callbacks.html) as a command line argument. 
- It adds the [`myerson`](https://github.com/kochgroup/myerson) package as a dependency to generate node-explanations for `MolGraph` explanations.
- It implements the `MyersonExplainerCallback` which can be submitted to the `predict` subcommand. 

## Desired workflow

### Command line usage:

```sh
chemprop predict --test-path tests/data/regression.csv \
    --model-path train_example/model_0/best.pt \
    --preds-path train_example/predictions.csv \
    --callback myerson
```
In addition to the `predictions.csv` file, the callback will generate a `predictions_myerson_explanation.pkl` file with the generated explanations.

### Programmatic usage

<details>
<summary>Click here to expand</summary>

```py
# Run in interactive window
# %% model training
import lightning.pytorch as pl
from chemprop import data, models, nn

# dummy data (find hydroxy groups)
smiles = ['c1ccccc1O', 'Cc1ccccc1O', 'CCc1ccccc1O', 'CCCc1ccccc1O', 'Cc1c(C)cccc1O',
 'c1ccccc1', 'Cc1ccccc1', 'CCc1ccccc1', 'CCCc1ccccc1', 'Cc1c(C)cccc1']
labels = [3.3, 3.3, 3.3, 3.3, 3.3, -2.5, -2.5, -2.5, -2.5, -2.5]
all_data = data.MoleculeDataset([data.MoleculeDatapoint.from_smi(smi, [y]) for smi, y in zip(smiles, labels)])
train_loader = data.build_dataloader(all_data, shuffle=False)

# train model 
mp = nn.BondMessagePassing()
agg = nn.MeanAggregation()
ffn = nn.RegressionFFN()
model = models.MPNN(mp, agg, ffn)
print('model instantiated')
trainer = pl.Trainer(
    logger=False,
    enable_checkpointing=False,
    max_epochs=150, # intentional overfit
    # callbacks=[] # here we could also add callbacks
)
trainer.fit(model, train_loader)
predictions = trainer.predict(model, train_loader) # with the callback we would get the explanations

# %% generate an explanation
from myerson.chemprop_explain import MyersonExplainer
# Sampling explainer for larger graphs:
# from myerson.chemprop_explain import MyersonSamplingExplainer

graph = all_data[0].mg
explainer = MyersonExplainer(graph, model)
my_values = explainer.calculate_all_myerson_values()
print(f"my_values=\n{my_values}")

# %% draw the explanations as heatmap
from rdkit import Chem
from rdkit.Chem.Draw import SimilarityMaps
from rdkit.Chem import Draw
from IPython.display import SVG, display

mol = Chem.MolFromSmiles(smiles[0])
d2d = Draw.MolDraw2DSVG(550,350)
SimilarityMaps.GetSimilarityMapFromWeights(mol, list(my_values), d2d)
d2d.FinishDrawing()
display(SVG(d2d.GetDrawingText()))
# ==> the hydroxy group contributes positively
```

</details>


## Questions
I can't build the docs (not just with the added/modified `.rst` files, also on a fresh clone).


## Checklist
- [x] linted with flake8?
- [x] (if appropriate) unit tests added?

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `7033cac6ebc1`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
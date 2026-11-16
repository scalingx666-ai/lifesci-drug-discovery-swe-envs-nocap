# Issue

**Title:** fixed_layers is never applied in vecmsani.train() / msani.train()

## Description

Both accept `fixed_layers` in `hyperparameters` and never use it, so every layer
is fine-tuned and nothing is logged. I do not think this was the intended behavior. Both classes already have a working
`fix_layers()` (`vecmsani.py:856`, `torchani_interface.py:1710`) but never call it. This is different from `class ani` which does call `fix_layers()`.

Proposed fix, the same what `ani.train()` does (line 474 in torchani_interface.py):

```python
        # fix layers
        if 'fixed_layers' in hyperparameters:
            self.fix_layers(getattr(hyperparameters['fixed_layers'], 'value',
                                    hyperparameters['fixed_layers']))
```

<details>
<summary>Test script — no data files, prints the trainable-parameter count</summary>

The python script below can be used to verify that fix_layers is never applied when vecmsani.train() is called.

```
loaded             1,365,063 trainable parameters
after train()      1,365,063 trainable parameters   <- fixed_layers ignored
after fix_layers()   144,935 trainable parameters   <- the method train() never calls
```

```python
import os
import numpy as np
import mlatom as ml

model_dir = ml.methods(method="OMNI-P2x").mlatom_model_dir
model = ml.vecmsani(model_file=os.path.join(model_dir, "OMNIP2x_CV_1.pt"),
                    nstates=3, verbose=0)
trainable = lambda: sum(p.numel() for p in model.model.parameters() if p.requires_grad)
print(f"loaded             {trainable():>10,} trainable parameters")

mol = ml.data.molecule()
mol.read_from_numpy(species=np.array(["O", "H", "H"]),
                    coordinates=np.array([[0., 0., 0.], [0., 0., .96], [.93, 0., -.24]]))
mol.electronic_states = [mol.copy() for _ in range(3)]
for j, state in enumerate(mol.electronic_states):
    state.energy = -76.0 + 0.1 * j

model.train(molecular_database=ml.data.molecular_database([mol]),
            validation_molecular_database=ml.data.molecular_database([mol]),
            property_to_learn="energy", save_model=False,
            hyperparameters={"fixed_layers": [[0, 4]], "max_epochs": 1,
                             "batch_size": 1, "learning_rate": 1e-3})
print(f"after train()      {trainable():>10,} trainable parameters")

model.fix_layers([[0, 4]])
print(f"after fix_layers() {trainable():>10,} trainable parameters")
```
</details>

Tested with MLatom 3.25.4.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `311e62543c3d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
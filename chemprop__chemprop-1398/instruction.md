# Issue

**Title:** Reject external data files with separate data paths

## Description

## Description

When two or three files are supplied to `--data-path`, the same row-aligned external data file is currently loaded independently for every split. Each load starts at row zero, so a shared descriptor matrix can silently attach training rows to validation and test molecules.

Multiple data paths are already documented as unsupported with external feature and descriptor files, and the implementation discussion in #1276 explicitly left that combination unsupported. This PR enforces that contract early instead of allowing corrupted associations. The validation covers datapoint descriptors, atom/bond features and descriptors, and atom/bond constraint data.

## Example / Current workflow

This clean-room reproducer uses three synthetic molecules and one descriptor matrix on the current `main` branch:

```python
from pathlib import Path
from tempfile import TemporaryDirectory

import numpy as np
import pandas as pd
from configargparse import ArgumentParser

from chemprop.cli.train import TrainSubcommand, build_splits

with TemporaryDirectory() as tmp:
    root = Path(tmp)
    paths = []
    for split, smiles in zip(("train", "val", "test"), ("C", "CC", "CCC")):
        path = root / f"{split}.csv"
        pd.DataFrame({"smiles": [smiles], "target": [0.0]}).to_csv(path, index=False)
        paths.append(path)

    descriptors = root / "descriptors.npz"
    np.savez(descriptors, np.array([[1.0], [2.0], [3.0]]))
    args = TrainSubcommand.add_args(ArgumentParser()).parse_args([
        "--data-path", *map(str, paths),
        "--descriptors-path", str(descriptors),
        "--output-dir", str(root / "out"),
    ])
    format_kwargs = dict(
        no_header_row=args.no_header_row, smiles_cols=args.smiles_columns,
        rxn_cols=args.reaction_columns, target_cols=args.target_columns,
        ignore_cols=args.ignore_columns, splits_col=args.splits_column,
        weight_col=args.weight_column, bounded=False,
    )
    featurization_kwargs = dict(
        molecule_featurizers=args.molecule_featurizers, keep_h=args.keep_h,
        add_h=args.add_h, ignore_stereo=args.ignore_stereo,
        reorder_atoms=args.reorder_atoms,
        use_cuikmolmaker_featurization=args.use_cuikmolmaker_featurization,
    )
    splits = build_splits(args, format_kwargs, featurization_kwargs)
    observed = [(part[0][0][0].name, part[0][0][0].x_d.item()) for part in splits]
    print(observed)
    assert observed == [("C", 1.0), ("CC", 2.0), ("CCC", 3.0)]
```

Current output is `[('C', 1.0), ('CC', 1.0), ('CCC', 1.0)]`, and the final assertion fails. The same row-zero reuse was independently reproduced for `--constraints-path`.

## Bugfix / Desired workflow

The public CLI now rejects the unsupported combination before building datasets:

```text
--descriptors-path is not supported with separate data files supplied to --data-path.
```

The regression test covers both two- and three-file inputs against all six row-aligned external-data flags. Single-file workflows and multiple data files without external row-aligned files are unchanged.

## Questions

None.

## Relevant issues

This closes the validation gap left by the multiple-data-path implementation in #1276. I did not find an existing issue for the silent row association.

## Checklist

- [x] linted with flake8?
- [x] unit tests added?

Focused verification: `20 passed` across the new validation tests and the adjacent train-argument unit tests. `flake8`, `isort --check-only`, Black 23, and `git diff --check` pass for the changed files.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b904ada665a3`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
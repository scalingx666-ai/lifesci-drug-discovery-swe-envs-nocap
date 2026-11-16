# Issue

**Title:** Fix hpopt default save dir bug

## Description

There are two bugs in hpopt that don't get caught by our tests. 

The first is
```
chemprop hpopt -i tests/data/regression/mol/mol.csv 
  File "/home/knathan/chemprop/chemprop/cli/hpopt.py", line 278, in process_hpopt_args
    args.hpopt_save_dir = Path(f"chemprop_hpopt/{args.data_path.stem}")
                                                 ^^^^^^^^^^^^^^^^^^^
AttributeError: 'list' object has no attribute 'stem'
```
This doesn't get caught because all our tests supply a value for `--hpopt-save-dir`. I don't think we need to change this because normally for tests you use the pytest temporary directories. I could be wrong and maybe we should change one of the tests.

The second is something like
```
chemprop hpopt -i tests/data/regression/mol/mol.csv 

with open(Path(args.output_dir) / "splits.json", "w") as f:
...
FileNotFoundError: [Errno 2] No such file or directory: 'chemprop_training/mol/2026-07-31T15-22-29/splits.json'
```
The output_dir is made in `TrainSubcommand.func` which isn't run during hpopt. But in our tests we first run training and then hpopt all within the same python call so the default dir `CHEMPROP_TRAIN_DIR / args.data_path[0].stem / NOW` keeps the same value (NOW is fixed once imported), so the directory can be reused in hpopt. 
This works on main:
```
pytest tests/cli/test_cli_regression_mol.py::test_train_quick tests/cli/test_cli_regression_mol.py::test_hyperopt_quick
```
While this doesn't:
```
pytest tests/cli/test_cli_regression_mol.py::test_hyperopt_quick
```
My solution is just to port the dir creation to `HpoptSubcommand.func`. Though I am very surprised this hasn't been opened as an issue before? An undergrad student I was working with showed me these errors, so I would think other users have run into them. They can both be overcome by just specifying `--hpopt-save-dir` and `--output-dir`, but still, wouldn't have someone opened an issue?

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `68fb56a47c94`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
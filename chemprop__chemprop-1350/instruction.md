# Issue

**Title:** Fix `--descriptors-columns` compat with `pandas>=3`

## Description

This line of code worked with previous versions of `pandas` because it would (unintentionally) return a copy, but in modern pandas it returns a view which is not writeable, causing this error during execution:

```
Wrote config file to output/fold_0/config.toml
Traceback (most recent call last):
  File "/home/jackson/miniconda3/envs/chemeleon_atropisomers/bin/chemprop", line 6, in <module>
    sys.exit(main())
             ~~~~^^
  File "/home/jackson/miniconda3/envs/chemeleon_atropisomers/lib/python3.13/site-packages/chemprop/cli/main.py", line 85, in main
    func(args)
    ~~~~^^^^^^
  File "/home/jackson/miniconda3/envs/chemeleon_atropisomers/lib/python3.13/site-packages/chemprop/cli/train.py", line 116, in func
    main(args)
    ~~~~^^^^^^
  File "/home/jackson/miniconda3/envs/chemeleon_atropisomers/lib/python3.13/site-packages/chemprop/cli/train.py", line 2206, in main
    splits = build_splits(args, format_kwargs, featurization_kwargs)
  File "/home/jackson/miniconda3/envs/chemeleon_atropisomers/lib/python3.13/site-packages/chemprop/cli/train.py", line 1114, in build_splits
    train_data = [make_data(args.data_path[0])]
                  ~~~~~~~~~^^^^^^^^^^^^^^^^^^^
  File "/home/jackson/miniconda3/envs/chemeleon_atropisomers/lib/python3.13/site-packages/chemprop/cli/train.py", line 1096, in make_data
    return build_data_from_files(
        data_path,
    ...<7 lines>...
        **featurization_kwargs,
    )
  File "/home/jackson/miniconda3/envs/chemeleon_atropisomers/lib/python3.13/site-packages/chemprop/cli/utils/parsing.py", line 470, in build_data_from_files
    mol_data, rxn_data = make_datapoints(
                         ~~~~~~~~~~~~~~~^
        smiss,
        ^^^^^^
    ...<10 lines>...
        **featurization_kwargs,
        ^^^^^^^^^^^^^^^^^^^^^^^
    )
    ^
  File "/home/jackson/miniconda3/envs/chemeleon_atropisomers/lib/python3.13/site-packages/chemprop/cli/utils/parsing.py", line 387, in make_datapoints
    MoleculeDatapoint(
    ~~~~~~~~~~~~~~~~~^
        mol=molss[mol_idx][i],
        ^^^^^^^^^^^^^^^^^^^^^^
    ...<9 lines>...
        V_d=V_dss[mol_idx][i],
        ^^^^^^^^^^^^^^^^^^^^^^
    )
    ^
  File "<string>", line 14, in __init__
  File "/home/jackson/miniconda3/envs/chemeleon_atropisomers/lib/python3.13/site-packages/chemprop/data/datapoints.py", line 113, in __post_init__
    super().__post_init__()
    ~~~~~~~~~~~~~~~~~~~~~^^
  File "/home/jackson/miniconda3/envs/chemeleon_atropisomers/lib/python3.13/site-packages/chemprop/data/datapoints.py", line 37, in __post_init__
    self.x_d[np.isnan(self.x_d)] = NAN_TOKEN
    ~~~~~~~~^^^^^^^^^^^^^^^^^^^^
ValueError: assignment destination is read-only
```

This fixes it, and is backwards compatible with pandas 2 (which had this argument, but did not always returns views)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `673a87cacc73`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
# Issue

**Title:** TabPFN: Add ignore_pretraining_limits to classifiers and regressors

## Description

The parameter `ignore_pretraining_limits=True` removes the limit to use only 1000 samples for training. 


https://huggingface.co/Prior-Labs/TabPFN-v2-reg/discussions/2

Currently, the tool fails when training size > 1000 samples:

```
Traceback (most recent call last):
  File "/opt/galaxy/shed_tools/toolshed.g2.bx.psu.edu/repos/bgruening/tabpfn/ed78e1448387/tabpfn/main.py", line 167, in <module>
    train_evaluate(args)
  File "/opt/galaxy/shed_tools/toolshed.g2.bx.psu.edu/repos/bgruening/tabpfn/ed78e1448387/tabpfn/main.py", line 98, in train_evaluate
    classifier.fit(tr_features, tr_labels)
  File "/usr/local/lib/python3.12/contextlib.py", line 81, in inner
    return func(*args, **kwds)
           ^^^^^^^^^^^^^^^^^^^
  File "/usr/local/lib/python3.12/site-packages/tabpfn_common_utils/telemetry/core/decorators.py", line 321, in wrapper
    return _safe_call_with_telemetry(
           ^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "/usr/local/lib/python3.12/site-packages/tabpfn_common_utils/telemetry/core/decorators.py", line 365, in _safe_call_with_telemetry
    result = func(*args, **kwargs)
             ^^^^^^^^^^^^^^^^^^^^^
  File "/usr/local/lib/python3.12/site-packages/tabpfn/classifier.py", line 758, in fit
    ensemble_configs, X, y = self._initialize_dataset_preprocessing(
                             ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "/usr/local/lib/python3.12/site-packages/tabpfn/classifier.py", line 642, in _initialize_dataset_preprocessing
    X, y, feature_names, n_features, original_y_name = ensure_compatible_fit_inputs(
                                                       ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "/usr/local/lib/python3.12/site-packages/tabpfn/validation.py", line 75, in ensure_compatible_fit_inputs
    validate_dataset_size(
  File "/usr/local/lib/python3.12/site-packages/tabpfn/validation.py", line 137, in validate_dataset_size
    _validate_num_samples_for_cpu(
  File "/usr/local/lib/python3.12/site-packages/tabpfn/validation.py", line 274, in _validate_num_samples_for_cpu
    raise RuntimeError(
RuntimeError: Running on CPU with more than 1000 samples is not allowed by default due to slow performance.
To override this behavior, set the environment variable TABPFN_ALLOW_CPU_LARGE_DATASET=1 or set ignore_pretraining_limits=True.
Alternatively, consider using a GPU or the tabpfn-client API: https://github.com/PriorLabs/tabpfn-client
```

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `16cb5bf9eb4a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
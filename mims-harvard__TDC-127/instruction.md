# Issue

**Title:** feat: Add interface for multi-instance splitting

## Description

Addressing #126 (support for multi-instance splitting). 
This is a draft PR, please give some feedback @kexinhuang12345 

**Done:**
Following your suggestion, I implemented a method called `create_fold_setting_cold_multi` that splits on multiple instance. I tried to follow the package conventions in coding style. The code logic is to iterate over all entities on which the split should be done (e.g., `['Drug_ID', 'Cell Line_ID']`) and randomly assign entity-instances to test. The test-set is created by selecting samples where **all** entity instances belong to test. This is then repeated for validation.
The proposed method is strictly more powerful than the current `create_fold_setting_cold`. Indeed, if a single entity is passed for splitting the result is always identical. I verified like this for multiple configurations.
```py
folds_1 = create_fold_setting_cold_multi(df, 42, [0.8, 0.1, 0.1], entities=['Drug_ID'])
folds_2 = create_fold_setting_cold_multi(df, 42, [0.8, 0.1, 0.1], entity='Drug_ID')

for a,b in zip(folds_1.values(), folds_1.values()):
    assert all(a==b)

```
Therefore, I wanted to suggest to replace the current `create_fold_setting_cold` with the body of the new `create_fold_setting_cold_multi`. This would be perfectly backwards compatible. The only difference would be that for the positional `entity` argument, instead of a `str` you could **also** pass a List of strings. The beauty of this solution is that it would avoid duplicate code snippets and require minimal updates in the existing codebase. Let me know what you think

**ToDo:**
- Decide whether `create_fold_setting_cold` is superseded by `create_fold_setting_cold_multi`
- Add an example to the docs
- unittests. Do you want to see some?
- Remove the print commands (I added them for debugging)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0e2611e35268`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
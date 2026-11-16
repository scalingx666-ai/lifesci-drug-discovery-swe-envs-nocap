# Issue

**Title:** fix use of bounded-loss in CLI with pandas 3

## Description

## Description
I want to use the chemprop CLI with pandas 3 but it doesn't work. The issue is that `applymap` is used in `chemprop/cli/utils/parsing.py`. This function has been deprecated for a while and is not available anymore in pandas 3 (see [here](https://pandas.pydata.org/pandas-docs/version/2.2/reference/api/pandas.DataFrame.applymap.html)). The recommendation is to use `map` instead. I applied this change, and the fixed code seems to work with both pandas 2 and 3, in my eyes.

The code section with the issue is not covered by test, so I added a small test.

## Example / Current workflow
When I have Pandas 3 installed, using latest main (commit db0bb86fbad6f6ec3c414202810390d8acc8baa0), I get an error when I run following command

```
chemprop train -i tests/data/regression/bounded.csv --target-columns logSolubility -l bounded-mse

[...]
AttributeError: 'DataFrame' object has no attribute 'applymap'
```

## Bugfix / Desired workflow
With the fix it works
```
$  chemprop train -i tests/data/regression/bounded.csv --target-columns logSolubility -l bounded-mse

[...]
2026-10-16T08:15:52 - INFO:chemprop.cli.train - Test Set results:
2026-10-16T08:15:52 - INFO:chemprop.cli.train - test/mse: 0.7898399233818054
2026-10-16T08:15:52 - INFO:chemprop.cli.train - Best model saved to 'chemprop_training/bounded/2026-10-16T08-15-46/model_0/best.pt'
```

## Questions
-

## Relevant issues
-

## Checklist
- [x] linted with flake8?
- [x] (if appropriate) unit tests added?

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5e1f6c32189a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
# Issue

**Title:** callback function for GA, file-based progress tracking

## Description

The GA function now accepts a user-defined callback-function, in the systax given by pymoo:

```python
    def _callback(algorithm):
        callback_path.write_text(f"generation={algorithm.n_gen}\n", encoding="utf-8")

    x_opt, f_opt = run_ga(
        data_model=optimizer,
        domain=ga_domain,
        objective_callables=[ga_objective],
        q=1,
        callable_format="torch",
        callback=_callback,
    )
 ```
 
 For the high-level acquisition optimization, a default function is defined which exports basic stats to a user-specified csv file:
 
 ```python
optimizer = strategies_data_models.GeneticAlgorithmOptimizer(
    population_size=100,
    n_max_gen=100,
    verbose=False,
    # Write per-generation GA progress so it can be inspected while optimization runs.
    ga_progress_csv_path="_custom_ga_progress.csv",
)
```

This can then be tracked by other processes during execution and may be used for status updates in web-apps etc.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `41d9edb1bcad`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
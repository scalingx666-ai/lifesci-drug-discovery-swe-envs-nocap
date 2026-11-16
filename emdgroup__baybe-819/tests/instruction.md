# Issue

**Title:** Add _ReducedSearchSpace for parameter-only reduced search spaces

## Description

Introduces `_ReducedSearchSpace` (private `SearchSpace` subclass) that exposes only parameter information without building the expensive discrete Cartesian product. This is constructed via `SearchSpace._drop_parameters(names)`, which returns a reduced version with the specified parameters removed.

 The class blocks access to anything beyond parameter-related properties.

  **Motivation**

  When building composite GP kernels, we need to call kernel factories on search spaces with certain parameters stripped away. A full `SearchSpace.from_product()` would rebuild the entire discrete candidate set. `_ReducedSearchSpace` avoids this by storing the parameter tuple directly and computing everything from it.

  **Changes to `SearchSpace` and kernel factories**

 The reduced search space exposes only name-based properties, no integer indices. To support this, we made two changes to existing code:

  - **Replaced `task_idx` sentinel checks** with `n_tasks > 1` / `n_tasks == 1` in kernel factories and fit criterion factories. (Equivalent because `TaskParameter` requires a minimum of 2 values).
  - **Added `SearchSpace._get_n_comp_rep_columns(selector)`** that returns the number of comp-rep columns for a parameter selection. This replaces the previous `len(get_comp_rep_parameter_indices(...))` in `_get_effective_dimensionality`, avoiding the need to expose index-returning methods on the reduced space. Uses `sum(len(p.comp_rep_columns) for p in params)` instead of delegating to `get_comp_rep_parameter_indices`.

  **Design of `_ReducedSearchSpace`**

  - Subclasses `SearchSpace` so it passes type checks and works with existing factory signatures
- Builds real `SubspaceDiscrete`/`SubspaceContinuous` instances with zero-row DataFrames so that `parameters`, `parameter_names`, and `comp_rep_columns` work correctly
  - Overrides `__getattribute__` with an allowlist — accessing `transform`, `index`, etc. raises `AttributeError` 

  **Allowed attributes**

  ```python
  _ALLOWED_ATTRIBUTES: ClassVar[frozenset[str]] = frozenset({
      "discrete",
      "continuous",
      "parameters",
      "parameter_names",
      "comp_rep_columns",
      "constraints",
      "type",
      "_task_parameter",
      "n_tasks",
      "_get_n_comp_rep_columns",
      "get_parameters_by_name",
      "_ALLOWED_ATTRIBUTES",
  })
  ```
**Outlook**

  This class is a building block for kernel override dispatching in the GP surrogate. The dispatching logic will:
  - Strip the task parameter from the search space
  - Call kernel factories on the reduced space to obtain a base kernel
  - Separately construct the task kernel
  - Multiply both at the gpytorch level after resolving indices against the full search space
  - Ensure that factories called on a reduced search space return BayBE Kernel objects (which use parameter names) rather than raw gpytorch kernels (which bake in integer indices)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `7d163ef9be36`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
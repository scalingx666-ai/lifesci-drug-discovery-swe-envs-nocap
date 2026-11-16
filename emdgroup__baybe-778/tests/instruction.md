# Issue

**Title:** Refactor searchspace attributes

## Description

Cleans up the internal architecture of the search space subclasses by removing legacy
attributes, simplifying interfaces, improving validation, and adding proper deprecation
paths for backward compatibility.

### Interface simplification
- `SubspaceContinuous` no longer requires users to manually group constraints by type;
  constraints are now grouped internally
- Dropped `empty_encoding` attribute from `SubspaceDiscrete`
- Dropped `comp_rep` parameter from `SubspaceDiscrete.__init__`

### Validation improvements
- Streamlined validation logic: `validate_parameters` and `validate_constraints` are now
  the sole entry points for parameter and constraint validation; internal helpers
  (`validate_parameter_names`, `validate_cardinality_constraints_are_nonoverlapping`,
  `validate_cardinality_constraint_parameter_bounds`) have been inlined or made private;
  `SearchSpace`-level invariants (non-empty collection, `TaskParameter` count) are now
  enforced exclusively at the `SearchSpace` level; this implicitly fixes missing
  validation for duplicate parameter names in `SubspaceDiscrete` and for constraint
  parameters referencing nonexistent parameters in both subspace classes
- Moved and consolidated search space validation tests to `tests/validation/`

### Deprecation handling
- Added deprecation mechanism for legacy `SubspaceDiscrete` arguments (`empty_encoding`,
  `comp_rep`)
- Added deprecation mechanism for legacy constraint arguments in `SubspaceContinuous`
  (grouped constraint lists)
- Added deserialization support for legacy `SubspaceDiscrete` format via custom cattrs
  hook

### Code quality
- Fixed class and attribute docstrings for both subspace classes
- Added missing attribute docstrings
- Dropped dead code (column subselection that would cause recursion) #797 

### Testing
- Added validation tests for both subspace classes (duplicate params, nonexistent
  constraint params)
- Added deserialization test for legacy `SubspaceDiscrete` format
- Parametrized tests and added hybrid search space case
- Added missing test step for toggled candidates recommendation

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `af00b3ee4466`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
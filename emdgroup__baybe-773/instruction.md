# Issue

**Title:** Smartly Apply Constraints During Cartesian Product

## Description

This PR implements a more optimized Cartesian product creation in the presence of constraints which can result in memory and time gains of many orders of magnitude (see mini benchmark below).

### Rationale
- Currently constraint filtering is done only after the entire search space has been created. This means the memory needed for the intermediate df is potentially huge even if the final df is tiny. In practice this had led to many problems when working with slot based mixtures, even if the optimized `from_simplex` constructor was used
- Instead, any given cosntraint can be applied early during the parameter-by-parameter cross join operations. There are three tiers of applying this:
  1) `As soon as possible filter`: A constraint can be applied as soon as all of its affected parameters are in the current crossjoin-df. After this application the constraint is fully ensured and does not have to be applied again. If the order in which cross join goes over the parameters is optimized this would already lead to an improvement as subsequent operations "see" much smaller left-dataframes.
  2) `Partial/early filter`: 
    - Some constraints can be applied even if not all affected parameters are present yet.
    - Example: no label duplicates - even if there are just 2 out of 7 parameters present, we can remove the rows that have duplicates in the 2 parameters.
    - This filter has to be repeated in every loop iteration until it ran with all affected parameters present. However, the cost of multiple filter applications are dwarfed by the savings from smaller cross join operations.
    - Whether a constraint supports early filtering might depend on its configuration, example: exclude constraint with combiner (early filter supported for OR, not for AND or XOR) 
  3) `Look ahead`: Some constraints can look ahead based on the possible parameter values that might be incoming and recognize that constraints cannot be fulfilled even in future crossjoin iterations.
    - This is essentially what `from_simplex` implements for the very special case of 1 global sum constraint and 1 cardinality constraint. If we ever implement look-ahead filters for all constraints the `from_simplex` constructor might become obsolete 
    - For this we would need access to the parameter values inside the constraint logic, which might be easier to implement once the constraints have been refactored #517  
- This PR implements smart filtering for tiers 1 and 2. I left `IMPROVE` notes to remember about tier 3. To achieve this
  - `Constraint.get_invalid` was extended to handle situations where not all parameters are in the df to be filtered. The constraint can the decide whether it can apply early filtering or returns the new `UnsupportedEarlyFilteringError` if it needs all parameters present
  - The crossjoin is done in a custom loop inside `parameter_cartesian_prod_pandas_constrained` which itself performs the process described above after deciding on a smart parameter order for the crossjoin

### Good To Know
- new Constraint method `has_polars_implementation`, discussion 
- new Constraint property `_filtering_parameters`, discussion  
- strange appearance of `DiscreteNoLabelDuplicatesConstraint` in `DiscretePermutationInvarianceConstraint .get_invalid` explained 

### Mini Benchmark:
- Scenario 1: 7 categoricals with 8 values each and a no label dupe constraint
- Scenario 2: complex slot-based mixture with 4 slots, 2 subgroups, sum constraints and additional product parameters
- Scenario 3: like scenario 2 but with 6 slots and 3 subgroups
- tested on (old main vs this branch) x (polars on/off) 
- 30min as max runtime for a quick test 

| Scenario | Polars | main | feature | Speedup | Memory reduction |
|---|---|---|---|---|---|
| **1**: `from_product`, 7×8 cat, NoLabelDuplicates (2M→40K rows) | OFF | 61.4s / 636 MB | 6.6s / 48 MB | **9.3x** | **13.2x** |
| | ON | 1.8s / 73 MB | 1.6s / 47 MB | 1.1x | 1.6x |
| **2**: `from_simplex`, 4-slot mixture + 3 extras (~4.5M→2.4K rows) | OFF | 14.7s / 62MB | 0.09s / 1.5 MB | **163x** | **41x** |
| | ON | 14.8s / 62MB | 0.53s / 7.3 MB | **28x** | **8.5x** |
| **3**: `from_simplex`, 6-slot mixture + 3 extras (~12B→22K rows) | OFF | >30min | 0.5s / 17 MB | **>3600x** | — |
| | ON | >30min | 0.5s / 17 MB | **>3600x** | — |

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `58eb538d2d5e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
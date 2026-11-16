# Issue

**Title:** Feature/add ga optimizer

## Description

PR for adding a genetic algorithm (pymoo) to BoFire.

`GeneticAlgorithm` is the second option, besides `BotorchOptimizer`, but works similar:

- All `q` experiments are optimized simultaneously. That means, that the dimension of the problem is `d*q`. A sequential mode could be implemented later.

**UPDATE: Variable Types**
- `CategoricalInput` variables, which are treated as one-hot-encoded columns by the model and the acquisition functions, are turned into categorical variables for the GA optimization. In the objective function, these categorical variables are transformed to one-hot-encoded tensors. The object `BofireDomainMixedVars` handles this conversion.
- `CategoricalDescriptorInput` is also transformed in to a categorical pymoo variable, but transformed into the descriptor space
- `DiscreteInput` will be converted to an pymoo Integer.

All transformations are handled in the helper class `BofireDomainMixedVars` 

**Constraints**
The GA cannot handle equality constraints well. Constraints are therefor handled differently:

- Constraints of the type `LinearEqualityConstraint`, `LinearInequalityConstraint`, and `NChooseKConstraint` are handled in a "repair-function". This repair function is used by the GA to map all individuals from the population $x$ to the feasible space $x'$. In this case, I implemented a repair-function for an arbitrary mixture of linear equality and inequality constraints with a quadratic programming approach:

$$
\min_{x'} \left( ||x-x' ||_2^2 \right)
$$

s.t.

$$
A \cdot x' = b
$$

$$
G \cdot x' <= h
$$

$$
lb <= x' <= ub
$$ 

The `NChooseKConstraint` is also handled in the reapir function: For each experiment in the population, the smallest factors are set to 0, if the *max_features* constraint is violated, and the upper bound of the largest feactors is set to an offset (defaults to $1e-3$), if the *min_features* constraint is violated.

The repair functions are handled in the class `LinearProjection`.

- Other supported constraints are: `ProductInequalityConstraint` and `NonlinearInequalityConstraint`. `ProductInequalityConstraint` are evaluated by the torch-callable, provided by the `get_nonlinear_constraints` function. `NonlinearInequalityConstraint` are evaluated from the experiments data-frame, by the constraints `__call__` method.


These are handled by the optimizer.

`NonlinearEqualityConstraints` are not supported.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `4f1a3ed08b1d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
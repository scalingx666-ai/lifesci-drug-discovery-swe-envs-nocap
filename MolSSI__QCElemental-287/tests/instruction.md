# Issue

**Title:** Feature normalize and standardize objects

## Description

<!-- Thank you for your contribution! -->

## Description
The purpose of this PR is to standardize the interface for input and result objects. It also removes duplicate field specifications by moving common attributes to parent classes. The general interface for most end user objects remains _almost_ the same, with a few tweaks to create the commonalities.

 

## Changelog description
- Refactored `Input` and `Result` objects to conform to a standard interface for each object type. Inspiration was drawn from existing implementations in `qcelemental` and extended to create consistency. 
- All input objects (`AtomicInput`, `OptimizationInput`, `TorsionDriveInput`) conform to the basic interface of `.molecule`, containing the initial molecule on which to perform/start the computation, and `.specification` which defines the `keywords`, `program`, `extras`, `protocols`, and other parameters to fully specify the computation. `molecule` + `specification` = complete computation. More sophisticated specifications, like `OptimizationSpecification` and `TorsionDriveSpecification` can be composed by adding `specifications` objects that define the collection of computations needed to execute the procedure. See `OptimizationSpecification` for an example that composes `AtomicSpecification` into it.
- All result objects (`AtomicResult`, `OptimizationResult`, `TorsionDriveResult`, `FailedOperation`) conform to the basic interface of `.input_data` which is a perfect copy of the input data used to generate the computation, `.success` boolean to define whether the operation succeeded or failed, and the `stdout` and `stderr` for the computation. Additionally, computation-specific output fields an be added as needed.
- All other properties found on inputs/outputs (like `id`, `schema_name` etc) were unmodified in form but refactored to parent classes to reduce duplicate code.

## Status
<!-- Please `pip install .[lint]; make format` in the base folder. -->
- [ x] Code base linted
- [ x] Community discussion has been had!
- [ x] With community approval for the design I'll update tests and get the code ready to go.
- [ x] Ready to go

## Interface description

This PR makes all interfaces conform to the following basic specification:

### Input Objects

All input objects (`AtomicInput`, `OptimizationInput`, `TorsionDriveInput`, future procedures...) follow the same pattern:
1. `.specification` specifies how that computation is to be performed. It contains all the `keywords`, `extras`, `protocols`, possible `model`/`driver`, and/or other fields required to be sent directly to the computational chemistry program being called.
2. `.molecule` attribute specifies on what molecule to perform (or begin) this operation.

The `Specification` objects take their inspiration from the `QCInputSpecification` object. Combining a specification with a molecule creates a computation as per .

Increasingly sophisticated computations (like procedures) can now be generated systematically by composition of any number of required `Specification` objects. A simplified `AtomicInput`, `OptimizationInput`, and `TorsionDriveInput` can be seen below that show how this pattern plays nicely at each level of abstraction.

```python
##### Specification Objects #####

class SpecificationBase(...):
    """Base specification directed at any computational chemistry program"""
    keywords: Dict[str, Any]
    program: str

class AtomicSpecification(SpecificationBase):
    """Specification for single point computations"""
    driver: DriverEnum
    model: Model

class OptimizationSpecification(SpecificationBase):
    """Specification for optimization procedures"""
    gradient_specification: AtomicSpecification

class TorsionDriveSpecification(SpecificationBase):
    """Specification for TorsionDrive procedures"""
    optimization_specification: OptimizationSpecification

##### Input Objects #####

class InputComputationBase(InputBase):
    """Base input directed at any computational chemistry program"""
    specification: SpecificationBase
    molecule: Molecule

class AtomicInput(InputComputationBase):
    r"""The MolSSI Quantum Chemistry Schema"""
    specification: QCInputSpecification 

class OptimizationInput(InputComputationBase):
    """Input object for an optimization computation"""
    specification: OptimizationSpecification

class TorsionDriveInput(InputComputationBase):
    """Inputs for running a torsion drive."""
    specification: TorsionDriveSpecification
```
### Result Objects

All result objects (`AtomicResult`, `OptimizationResult`, `TorsionDriveResult`, `FailedOperation`) conform to the same interface. The previous split between inheritance (on successful results) and composition (on failed results) is resolved in favor of composition. The inheritance from input objects created difficulty with `schema_name` that required special validation and the mixing of the `.extras` dictionary that contained both input and output values. Additionally, creating new inputs from previous results was difficult because the input and output fields were mixed on the same object so things like `AtomicInput(**my_old_atomic_result.dict())` raise exceptions. `AtomicInput(**my_old_atomic_result.input_data.dict()` would be nice. I preferred the ease of accessing the complete input data at `.input_data` on a `FailedOperation` object :) Grouping result objects via inheritance also eliminated field duplication. All result objects follow this interface:

1. `.success`: bool (`True` on all successful results, `False` on `FailedOperation`)
2. `.input_data`: The full input data object that created the computation
3. `.stdout`: Optional[str] of stdout data
4. `.stderr`: Optional[str] of stderr

Here is a simplified hierarchy:

```python

class ResultBase(InputResultBase):
    """Base class for all result classes"""

    input_data: InputBase = Field(..., description="The input data supplied to generate the computation")
    success: bool
    stdout: Optional[str] = None
    stderr: Optional[str] = None


class SuccessfulResultBase(ResultBase):
    """Base object for any successfully returned result"""

    success: Literal[True]

class AtomicResult(SuccessfulResultBase):
    r"""Results from a CMS program execution."""

    input_data: AtomicInput 
    properties: AtomicResultProperties
    wavefunction: Optional[WavefunctionProperties] 
    return_result: Union[float, Array[float], Dict[str, Any]
    native_files: Dict[str, Any] = {}

class OptimizationResult(SuccessfulResultBase):
    """The result of an optimization procedure"""

    input_data: OptimizationInput
    final_molecule: Optional[Molecule]  # Should this be optional? Seems necessary!
    trajectory: List[AtomicResult]
    energies: List[float]

class TorsionDriveResult(SuccessfulResultBase):
    """Results from running a torsion drive."""

    input_data: TorsionDriveInput
    final_energies: Dict[str, float]
    final_molecules: Dict[str, Molecule]
    optimization_history: Dict[str, List[OptimizationResult]]

class FailedOperation(ResultBase):
    """Record indicating that a given operation (program, procedure, etc.) has failed and containing the reason and input data which generated the failure."""

    input_data: Union[AtomicInput, OptimizationInput, TorsionDriveInput]
    success: Literal[False]
    error: ComputeError
```

This plays nicely with your brain because you can interact with all inputs and outputs in the same way. Inputs always contain a molecule and a specifications. Specifications always contains `program`, `keywords` for that program, and any additional `specifications` required for sub-computations (like a gradient specification for an optimization routine). All result objects have a `.success` value, `input_data` value, and then any additional fields unique to their computation type. I think these changes can make `qcelemental` even easier to use and more consistent to program with.

I consider this PR a starting point for community conversation! So I look forward to hearing feedback, thoughts, opinions, and concerns. Hope this can move `qcel` forward in a positive way. Thanks to all the maintainers for your work on the package.

## Simple Script

If you want to play with these objects and see how they feel just install `qcelemental` from this branch and then use this script (assuming you named it `hacking.py`).

```shell
python -i hacking.py
```

```python
from qcelemental.models import (
    Molecule,
    AtomicInput,
    AtomicResult,
    OptimizationInput,
    OptimizationResult,
    TorsionDriveInput,
    TorsionDriveResult,
)

water = Molecule.from_data(
    """
    0 1
    O  -1.551007  -0.114520   0.000000
    H  -1.934259   0.762503   0.000000
    H  -0.599677   0.040712   0.000000
    """
)

water_input_spec = {"model": {"method": "energy", "basis": "6g-31"}, "driver": "energy", "program": "psi4"}
ai = AtomicInput(
    molecule=water,
    specification=water_input_spec,
)
print(ai, "\n")
ar = AtomicResult(
    input_data=ai,
    return_result=123,
    provenance={"creator": "colton"},
    properties={},
)
print(ar, "\n")

water_gradient = {**water_input_spec, **{"driver": "gradient"}}
opt_spec = {"gradient_specification": water_gradient, "program": "fake_optimizer_program"}
oi = OptimizationInput(molecule=water, specification=opt_spec)
print(oi, "\n")

optres = OptimizationResult(
    input_data=oi,
    final_molecule=water,
    trajectory=[ar],
    provenance={"creator": "colton"},
    energies=[
        123,
        456,
    ],
)

print(optres, "\n")

tdi = TorsionDriveInput(
    molecule=water,
    specification={
        "keywords": {
            "dihedrals": ((1, 2, 3, 4), (1, 2, 3, 4)),
            "grid_spacing": [6, 7],
        },
        "optimization_specification": opt_spec,
        "program": "torsiondrive",
    },
)

print(tdi, "\n")

tdr = TorsionDriveResult(
    input_data=tdi,
    final_energies={"hi": 123.2},
    final_molecules={"water": water},
    optimization_history={"angle": [optres]},
    provenance={"creator": "colton"},
)

```

## Addendum
Because I was using `pyreverse` to model the various data relationships in the library I also took the liberty to delete the old models that were to be removed in `v0.13.0` since this made it easier to visualize the code.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `295642189fe3`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
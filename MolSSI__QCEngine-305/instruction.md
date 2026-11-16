# Issue

**Title:** Add torsiondrive compute procedure

## Description

<!-- Thank you for your contribution! -->

## Description
<!-- Provide a brief description of the PR's purpose here. -->

This PR implements an initial proof of concept `torsiondrive` procedure as outlined in issue #306.

There are a number of questions about this PR:

* As `qcelemental` does not have native models for torsion drives I created some here based off of the QCElemental optimisation models and the QCPortal torsion drive models. Are these something that could / should live in QCElemental?

* Is it more efficient to run multiple torsion drives at once, each with access to one core, or one torsion drive at once using all of the cores.

If the QCE maintainers would be happy to accept a PR similar to this I'd be happy to add an example / tests here.

An example input would look like:

```
molecule = Molecule(
    symbols=["C", "C", "H", "H", "H", "H", "H", "H"],
    connectivity=[
        (0, 1, 1),
        (0, 2, 1),
        (0, 3, 1),
        (0, 4, 1),
        (1, 5, 1),
        (1, 6, 1),
        (1, 7, 1),
    ],
    geometry=[
        1.5403406836914142, -1.0173082391323545, 0.9312810207342496,
        4.0719763300123235, -0.0975682592642413, -0.02203578938791481,
        0.0002563605701713713, 0.0013953403968729996, 0.0011121160323317373,
        1.309831306165048, -3.03614919350581, 0.5491856718564878,
        1.3800394103640543, -0.7181256543708329, 2.9707878359388222,
        5.6120991748009645, -1.1161249890160694, 0.907991575289461,
        4.302418801484787, 1.921022388748466, 0.36057345099334853,
        4.232223312568672, -0.3961916040297606, -2.061588178357897]
)

result = compute_procedure(
    input_data=TorsionDriveInput(
        keywords={
            "dihedrals": [(2, 0, 1, 5)],
            "grid_spacing": [60]
        },
        input_specification=QCInputSpecification(
            driver=DriverEnum.gradient,
            model=Model(method="UFF", basis=None)
        ),
        initial_molecule=molecule,
        optimization_spec=OptimizationSpecification(
            procedure="geomeTRIC",
            keywords={
                "coordsys": "dlc",
                "maxiter": 300,
                "program": "rdkit",
            }
        )
    ),
    procedure="torsiondrive"
)

print(result)
```

Closed #306

## Changelog description
<!-- Provide a brief single sentence for the changelog. -->

Adds a new `torsiondrive` compute procedure

## Status
<!-- Please `pip install .[lint]; make format` in the base folder. -->
- [x] Code base linted
- [x] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e248d2fc0349`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
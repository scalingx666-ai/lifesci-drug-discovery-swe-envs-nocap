# Issue

**Title:** Implement Spinner optimizer with docs and tests.

## Description

Requested Reviewers: @lukasturcani 
*Note for Reviewers: If you accept the review request add a :+1: to this post*

Simply add another optimizer called Spinner, which is made to optimize/generate conformers of host-guest pairs. This is most crucial for systems with multiple guests that may have overlapping structures.

I followed the same approach as the mchammer optimizers (effectively the same interface and code).

Adds a new dependency. It is small, but worth making the decision about its inclusion.


minimum working example (tests also included) - compare the two output structures.:

```python
import stk

host = stk.ConstructedMolecule(
    topology_graph=stk.cage.FourPlusSix(
        building_blocks=(
            stk.BuildingBlock('BrCCBr', [stk.BromoFactory()]),
            stk.BuildingBlock(
                smiles='BrCC(Br)CBr',
                functional_groups=[stk.BromoFactory()],
            ),
        ),
    ),
)
host = stk.BuildingBlock.init_from_molecule(host)
guest1_bb = stk.BuildingBlock('c1ccccc1')
guest1 = stk.host_guest.Guest(
    building_block=guest1_bb,
    start_vector=guest1_bb.get_direction(),
    end_vector=(1., 0., 0.),
    displacement=(0, 0, 0),
)
guest2_bb = stk.BuildingBlock('C1CCCC1')
guest2 = stk.host_guest.Guest(
    building_block=guest2_bb,
    start_vector=guest2_bb.get_direction(),
    end_vector=(0., 1., 0.),
    displacement=(0, 0, 0),
)

complex.write('complex_2.mol')
complex = stk.ConstructedMolecule(
    topology_graph=stk.host_guest.Complex(
        host=host,
        guests=(guest1, guest2),
    ),
)
complex.write('complex_3.mol')

complex = stk.ConstructedMolecule(
    topology_graph=stk.host_guest.Complex(
        host=host,
        guests=(guest1, guest2),
        optimizer=stk.Spinner(),
    ),
)
complex.write('complex_3_opt.mol')

```

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `45170dee07c7`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
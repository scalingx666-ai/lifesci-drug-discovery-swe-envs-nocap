# Issue

**Title:** First attempt at multiple guests.

## Description

Related Issues: #351 
Requested Reviewers: @lukasturcani 

This PR is the beginnings of a new feature for the host_guest topology graph that allows for any number of guests to be placed inside a host. Currently, this is done by modifying the Complex API to take an iterable of `guests`, which are `.Guest(TopologyGraph)` classes. Unsure if that is the best approach, but it provides the needed methods and avoids i) a new type of class for the Guests ii) or expanding the `BuildingBlock` class or iii) an odd usage of a vertex as input to a TopologyGraph through a `.GuestVertex` class (my initial thought but nowhere else in stk is this done). 

Also tempted to have a `.Complex` and `.NGuestComplex` class so that the original method can be maintained for backwards compatibility.

Submitting this to get feedback, the placement of code in stk, tests, examples and docstrings are not complete.

* `src/stk/molecular/topology_graph/host_guest/complex.py:Complex.init()`: This method is simplified greatly and simply handles the transform of host and guests arguments into `building_block_vertices`
* 
* `src/stk/molecular/topology_graph/host_guest/complex.py`: Add new class (temporarily), `.Guest(TopologyGraph)` whose `init` is effectively equivalent to the old `Complex.init()` and handles the definition of the properties required to define a `GuestVertex`.


See the code below for building a structure with 1 or 2 guests:


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
    guest=guest1_bb,
    guest_start=guest1_bb.get_direction(),
    guest_target=(1., 0., 0.),
    displacement=(0, 0, 0),
)
guest2_bb = stk.BuildingBlock('C1CCCC1')
guest2 = stk.host_guest.Guest(
    guest=guest2_bb,
    guest_start=guest2_bb.get_direction(),
    guest_target=(0., 1., 0.),
    displacement=(0, 0, 0),
)

print(host, guest1, guest2)

complex = stk.ConstructedMolecule(
    topology_graph=stk.host_guest.Complex(
        host=host,
        guests=(guest1, ),
    ),
)
complex.write('complex_1.mol')
complex = stk.ConstructedMolecule(
    topology_graph=stk.host_guest.Complex(
        host=host,
        guests=(guest2, ),
    ),
)
complex.write('complex_2.mol')
complex = stk.ConstructedMolecule(
    topology_graph=stk.host_guest.Complex(
        host=host,
        guests=(guest1, guest2),
    ),
)
complex.write('complex_3.mol')

```

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1b556176ef79`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
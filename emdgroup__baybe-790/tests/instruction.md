# Issue

**Title:** Transfer Learning Decorator

## Description

DevPR, parent is 

Last piece to the puzzle:
Presets (i.e. papers, packages, etc) can dictate certain aspects of the GP model while not saying anything about other aspects. For example, both EDBO and CHEN focus on the kernel priors but don't even consider transfer learning at all. This is a general issue, and can also cover other things like multi-fidelity etc. 

For these cases, we want to follow the approach `if not defined, use BayBE default mechanism/setting`. However, this requires to abstract these settings/mechanism into reusable structures. This PR takes care of this step for transfer learning (which is currently the only mechanism that needs to be ported) in the form of a class decorator. Because other mechanisms will follow in the future and their extent isn't yet fully clear (e.g. multi-fidelity or transfer learning via mean injection), we keep this decorator private for now. A possible future extension of the decorator could have the form `@enable_mechanism(transfer_learning=True, multi_fidelity=True)` that then accepts any existing GP component and makes the necessary adjustments.

### Technical Details

The decorator supports two application modes to avoid name collisions in the subclass registry (used for serialization/deserialization):

1. `@` syntax (`@_enable_transfer_learning`): The decorated version replaces the original class entirely, so no two references coexist. The class is modified in-place, preserving its registry name.

2. Assignment syntax (`DecoratedX = _enable_transfer_learning(X, name="DecoratedX")`): Both the original and the decorated class must remain accessible and independently usable. A sibling class is created so both variants can coexist in the registry under distinct names.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `fd3fd213a390`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
# Issue

**Title:** Allow for multiprocessing spawn

## Description

Allows for multiprocessing 'start_method' to be defined outside of autodE. Required when calling, for example PyJulia. A minimal example is:


```python
import multiprocessing as mp
import autode as ade

mp.set_start_method("spawn", force=True)


def mol():
    return ade.Molecule(atoms=[ade.Atom('H'), ade.Atom('H', x=0.7)])


if __name__ == '__main__':

    with mp.Pool(2) as pool:
        res = [pool.apply_async(mol) for _ in range(2)]
        mols = [r.get() for r in res]
```

which gets stuck in an infinite loop. This PR adds a try-except block for setting and then skips calling functions with a timeout. If anyone knows how to keep both that would be great..

**NOTE**: As far as I'm aware the set_spawn method cannot be captured by codecov, but there is a test checking that it works.

---

- [x] Test
- [x] Update changelog
- [x] Rebase when #93 is merged

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `aa75457a9ebe`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
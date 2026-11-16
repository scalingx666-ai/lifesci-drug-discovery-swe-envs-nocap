# Issue

**Title:** Allowing torchani to use GPU

## Description

<!-- Thank you for your contribution! -->

## Description
Added config for torchani to use GPU, related to this issue  
Now we can use `local_options={'device':'cuda'}` to assign the device: 
```
import qcengine as qcng
import qcelemental as qcel

mol = qcel.models.Molecule.from_data("""
O  0.0  0.000  -0.129
H  0.0 -1.494  1.027
H  0.0  1.494  1.027
""")

inp = qcel.models.AtomicInput(
    molecule=mol,
    driver="energy",
    model={"method": "ani2x"}
    )

ret = qcng.compute(inp, "torchani", local_options={'device':'cuda'})
print(ret.return_result)
```

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0612e81a2ce6`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
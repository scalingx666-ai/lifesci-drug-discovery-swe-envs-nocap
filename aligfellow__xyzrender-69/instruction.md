# Issue

**Title:** More efficient cube parsing

## Description

Removes the call to `.join()` on the cube data, and just reads the data straight from the open file. This is ~50% faster.

Benchmarking code 

```python
import numpy as np
from xyzrender.cube import parse_cube
from pathlib import Path
import time

cubes = list(Path("examples/structures").glob("*.cube"))
cubedata = []
for cube in cubes:
    start = time.time()
    cubedata.append(parse_cube(cube))
    end = time.time()
    print(f"Parsed {cube} in {end - start:.4f} seconds")
```


```
# Old way
Parsed examples/structures/base-pair-dens.cube in 0.1696 seconds
Parsed examples/structures/base-pair-grad.cube in 0.1949 seconds
Parsed examples/structures/caffeine_dens.cube in 0.2795 seconds
Parsed examples/structures/caffeine_esp.cube in 0.2925 seconds
Parsed examples/structures/caffeine_homo.cube in 0.2927 seconds
Parsed examples/structures/caffeine_lumo.cube in 0.2890 seconds
Parsed examples/structures/phenol_di-dens.cube in 0.1385 seconds
Parsed examples/structures/phenol_di-grad.cube in 0.1224 seconds

# New way
Parsed examples/structures/base-pair-dens.cube in 0.0749 seconds
Parsed examples/structures/base-pair-grad.cube in 0.0895 seconds
Parsed examples/structures/caffeine_dens.cube in 0.1541 seconds
Parsed examples/structures/caffeine_esp.cube in 0.1308 seconds
Parsed examples/structures/caffeine_homo.cube in 0.1340 seconds
Parsed examples/structures/caffeine_lumo.cube in 0.1229 seconds
Parsed examples/structures/phenol_di-dens.cube in 0.0650 seconds
Parsed examples/structures/phenol_di-grad.cube in 0.0599 seconds
```

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `278a8148d5e7`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
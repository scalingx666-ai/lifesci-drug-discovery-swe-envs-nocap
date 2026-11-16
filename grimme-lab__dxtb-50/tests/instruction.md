# Issue

**Title:** Vectorize integral primitive

## Description

default @ 4736d8de6c101b0cceedd6312af16c49b4bfdfc3

```
❯ pytest test/test_hamiltonian/test_scf.py
= test session starts =
platform linux -- Python 3.8.13, pytest-7.1.2, pluggy-1.0.0
rootdir: /home/awvwgk/projects/src/git/torch/xtbML, configfile: pyproject.toml
collected 10 items

test/test_hamiltonian/test_scf.py .......... [100%]

= 10 passed in 9.81s =
```

This patch

```
❯ pytest test/test_hamiltonian/test_scf.py
= test session starts =
platform linux -- Python 3.8.13, pytest-7.1.2, pluggy-1.0.0
rootdir: /home/awvwgk/projects/src/git/torch/xtbML, configfile: pyproject.toml
collected 10 items

test/test_hamiltonian/test_scf.py .......... [100%]

= 10 passed in 1.84s =
```

Gives some gain.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `4736d8de6c10`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
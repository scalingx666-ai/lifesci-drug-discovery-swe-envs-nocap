# Issue

**Title:** Jupyterlab 0.27

## Description

```bash
cd [nglview root folder]
source devtools/nglview-jupyterlab.sh
jupyter-lab
```

NOTE: does not work with mirrored output yet: 

<img width="1087" alt="screen shot 2017-10-09 at 12 49 10 am" src="https://user-images.githubusercontent.com/4451957/31325483-b2bf4aae-ac8b-11e7-9c79-b4caba949a1f.png">

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `779ba932b886`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
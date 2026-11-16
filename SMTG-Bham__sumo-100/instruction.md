# Issue

**Title:** Plot PDOS from CASTEP

## Description

@ajjackson I have added the ability to plot CASTEP PDOS. The actual binary file is read using [castepxbin](https://github.com/zhubonan/castepxbin), which also does some processing such as assigning the angular moment channel to orbitals and orbitals sites.

A few things:

- I am not sure how the f orbitals in CASTEP relates to that in VASP. The latter does not have any meaningful labels, so I just naively assigned them in order they appear.
- I have only tested with the `Si2` example found in the CASTEP's tutorial. The generated PDOS plot is consistent with that of from OptaDos. 
- In the future, the dependency `castepxbin` will be released to pypi, I added its repo address and pinned to `v0.0.1` tag in the `setup.py` for now.

Si2 Example:
Left - OptaDOS
Right - Sumo
![image](https://user-images.githubusercontent.com/33688599/82557842-5e56c080-9b64-11ea-8343-9de4ee63e9ee.png)

### Testing instruction

First clone my repository (ideally in a new venv so there is no risk of messing up the current installation):

```
git clone https://github.com/zhubonan/sumo.git
```

Then checkout the `pr-castep-pdos` branch containing the update.

```
cd sumo
git checkout pr-castep-pdos
```

Once this is done, install the local repository using `pip`:

```
cd ../
pip install -e ./sumo
```

Afterwards, do your usual `sumo-dosplot -c castep -g 0.1`, it will print something like:

```
Found PDOS binary file Si2.pdos_bin, including PDOS in the plot.  
Reading CASTEP .bands file header...
nbands: 23, efermi / Ry: 0.165228, spin channels: 1
Reading band eigenvalues...
Electronic structure appears to have a bandgap
Setting energy zero to VBM
```

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d21ab01030f2`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
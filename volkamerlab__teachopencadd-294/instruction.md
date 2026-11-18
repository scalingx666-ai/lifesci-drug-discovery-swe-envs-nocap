# Issue

**Title:** T008/10/15/16/18/20: AttributeError: module 'numpy' has no attribute 'typeDict'

## Description

## Description

Fix `AttributeError: module 'numpy' has no attribute 'typeDict'` for T008/10/15/16/18/20.


Example: T008 fails for all OS and Python versions:
```
---------------------------------------------------------------------------
AttributeError                            Traceback (most recent call last)
Cell In[1], line 21
     18 from rdkit.Chem import Draw
     19 from rdkit.Chem import PandasTools
---> 21 from opencadd.structure.superposition.api import align, METHODS
     22 from opencadd.structure.core import Structure
     24 # Disable some unneeded warnings

File C:\Miniconda\envs\teachopencadd\lib\site-packages\opencadd\structure\superposition\api.py:7
      5 from .engines.theseus import TheseusAligner
      6 from .engines.mmligner import MMLignerAligner
----> 7 from .engines.mda import MDAnalysisAligner
      8 from ..core import Structure
     11 METHODS = {
     12     "theseus": TheseusAligner,
     13     "mmligner": MMLignerAligner,
     14     "mda": MDAnalysisAligner,
     15 }

File C:\Miniconda\envs\teachopencadd\lib\site-packages\opencadd\structure\superposition\engines\mda.py:8
      5 import logging
      7 import numpy as np
----> 8 from MDAnalysis.analysis import align as mda_align, rms
      9 from MDAnalysis.lib.util import canonical_inverse_aa_codes, convert_aa_code
     10 import biotite.sequence.align as align

File C:\Miniconda\envs\teachopencadd\lib\site-packages\MDAnalysis\__init__.py:207
    205 from .core.universe import Universe, Merge
    206 from .core.groups import AtomGroup, ResidueGroup, SegmentGroup
--> 207 from .coordinates.core import writer as Writer
    209 # After Universe import
    210 from .coordinates.MMTF import fetch_mmtf

File C:\Miniconda\envs\teachopencadd\lib\site-packages\MDAnalysis\coordinates\__init__.py:770
    768 from . import TRJ
    769 from . import TRR
--> 770 from . import H5MD
    771 from . import TRZ
    772 from . import XTC

File C:\Miniconda\envs\teachopencadd\lib\site-packages\MDAnalysis\coordinates\H5MD.py:218
    216 from MDAnalysis.lib.util import store_init_arguments
    217 try:
--> 218     import h5py
    219 except ImportError:
    220     HAS_H5PY = False

File C:\Miniconda\envs\teachopencadd\lib\site-packages\h5py\__init__.py:46
     37     _warn(("h5py is running against HDF5 {0} when it was built against {1}, "
     38            "this may cause problems").format(
     39             '{0}.{1}.{2}'.format(*version.hdf5_version_tuple),
     40             '{0}.{1}.{2}'.format(*version.hdf5_built_version_tuple)
     41     ))
     44 _errors.silence_errors()
---> 46 from ._conv import register_converters as _register_converters
     47 _register_converters()
     49 from .h5z import _register_lzf

File h5py\_conv.pyx:1, in init h5py._conv()

File h5py\h5t.pyx:293, in init h5py.h5t()

File C:\Miniconda\envs\teachopencadd\lib\site-packages\numpy\__init__.py:284, in __getattr__(attr)
    281     from .testing import Tester
    282     return Tester
--> 284 raise AttributeError("module {!r} has no attribute "
    285                      "{!r}".format(__name__, attr))

AttributeError: module 'numpy' has no attribute 'typeDict'
```
I checked if the `opencadd` package (`mamba create -n oc opencadd` install) shows the same fail but it does not. So how does `teachopencadd` differ?

Difference between (a) `teachopencadd` install (error) and (b) `opencadd` install (no error), versions:
`opencadd` same - 1.0.1
`mdanalysis` same -  2.3.0
`numpy` same - (a) 1.24.0 and (b) 1.24.0
`h5py` not the same - (a) 2.10.0 and (b) 3.7.0 because of `tensorflow` installation!

## Solution
- [x] Drop `tensorflow` pin and move it to the end of the env list
- [x] Remove `numpy` mention in `teachopencadd` env (was needed at some point to fix conflicts with `mdanalysis` but not needed anymore )
- [x] Remove T021/22 (who use `tensorflow`) from CI (deal with these notebooks in follow-up PR)
- [x] Pin `numpy`<1.24 and unpin `tensorflow` (see discussion [here](https://stackoverflow.com/questions/74852225/attributeerror-module-numpy-has-no-attribute-typedict))

## Status
- [x] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `4edc07bbaaeb`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
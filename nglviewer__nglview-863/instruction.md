# Issue

**Title:** Use mkstemp instead of NamedTemporaryFile in adaptor.py

## Description

This PR fixes the following kind of error on Windows:

```
---------------------------------------------------------------------------
PermissionError                           Traceback (most recent call last)
<ipython-input-15-6560b3ab8250> in <module>
      3 print(os.getcwd())
      4 traj = mdtraj.load('traj.pdb')
----> 5 nglview.show_mdtraj(traj)

~\.conda\envs\openmm\lib\site-packages\nglview\show.py in show_mdtraj(mdtraj_trajectory, **kwargs)
    293     '''
    294     structure_trajectory = MDTrajTrajectory(mdtraj_trajectory)
--> 295     return NGLWidget(structure_trajectory, **kwargs)
    296 
    297 

~\.conda\envs\openmm\lib\site-packages\nglview\widget.py in __init__(self, structure, representations, parameters, **kwargs)
    235         if isinstance(structure, Trajectory):
    236             name = py_utils.get_name(structure, kwargs)
--> 237             self.add_trajectory(structure, name=name, **kwargs)
    238         elif isinstance(structure, (list, tuple)):
    239             trajectories = structure

~\.conda\envs\openmm\lib\site-packages\nglview\widget.py in add_trajectory(self, trajectory, **kwargs)
   1138             trajectory = trajectory
   1139 
-> 1140         self._load_data(trajectory, **kwargs)
   1141         setattr(trajectory, 'shown', True)
   1142         self._trajlist.append(trajectory)

~\.conda\envs\openmm\lib\site-packages\nglview\widget.py in _load_data(self, obj, **kwargs)
   1206         if not is_url:
   1207             if hasattr(obj, 'get_structure_string'):
-> 1208                 blob = obj.get_structure_string()
   1209                 kwargs2['ext'] = obj.ext
   1210                 passing_buffer = True

~\.conda\envs\openmm\lib\site-packages\nglview\adaptor.py in get_structure_string(self)
    317 
    318     def get_structure_string(self):
--> 319         return _get_structure_string(self.trajectory[0].save_pdb)
    320 
    321 

~\.conda\envs\openmm\lib\site-packages\nglview\adaptor.py in _get_structure_string(write_method, suffix)
     43 def _get_structure_string(write_method, suffix='.pdb'):
     44     with NamedTemporaryFile(suffix=suffix) as fh:
---> 45         write_method(fh.name)
     46         return fh.read().decode()
     47 

~\.conda\envs\openmm\lib\site-packages\mdtraj\core\trajectory.py in save_pdb(self, filename, force_overwrite, bfactors)
   1389 
   1390 
-> 1391         with PDBTrajectoryFile(filename, 'w', force_overwrite=force_overwrite) as f:
   1392             for i in xrange(self.n_frames):
   1393 

~\.conda\envs\openmm\lib\site-packages\mdtraj\formats\pdb\pdbfile.py in __init__(self, filename, mode, force_overwrite, standard_names)
    271             self._header_written = False
    272             self._footer_written = False
--> 273             self._file = open_maybe_zipped(filename, 'w', force_overwrite)
    274         else:
    275             raise ValueError("invalid mode: %s" % mode)

~\.conda\envs\openmm\lib\site-packages\mdtraj\utils\zipped.py in open_maybe_zipped(filename, mode, force_overwrite)
     52             return io.TextIOWrapper(binary_fh, encoding='utf-8')
     53         else:
---> 54             return open(filename, 'w')
     55     else:
     56         raise ValueError('Invalid mode "%s"' % mode)

PermissionError: [Errno 13] Permission denied: 'C:\\Users\\AAAAAA\\AppData\\Local\\Temp\\tmpl9q5aei1.pdb'
```

NamedTemporaryFile creates a file that may not be readable on Windows. See https://docs.python.org/3.8/library/tempfile.html#tempfile.NamedTemporaryFile

@rasmusthog It seems that you stumbled upon this issue too () Can you try this patch? It works for my students who are using Windows and I tested it on my Linux system.

If you are working with a conda environment, you can install my patched version as follows:

```bash
conda install git
conda uninstall nglview
pip install git+https://github.com/tovrstra/nglview.git@fix_named_temp
```

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `12ab36c78dff`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
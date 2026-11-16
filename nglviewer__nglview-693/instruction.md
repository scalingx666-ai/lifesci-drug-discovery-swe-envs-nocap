# Issue

**Title:** Fix traitlets widget for large mdanalysis trajectories.

## Description

the traitlets widget expects a python int. I'm currently not sure if this is a
nglview or traitlets error. This cast is a band-aid solution though. There might be a better fix.

**Versions**

nglview: 1.0.a7
traitlets: 4.3.2
ipywidgets: 7.0.0

**Traceback**

```python
TraitError                                Traceback (most recent call last)
<ipython-input-38-e0520a7a97cf> in <module>()
----> 1 view = ng.show_mdanalysis(sim.universe)

~/anaconda3/lib/python3.6/site-packages/nglview-1.0a7-py3.6.egg/nglview/show.py in show_mdanalysis(atomgroup, **kwargs)
    290     '''
    291     structure_trajectory = MDAnalysisTrajectory(atomgroup)
--> 292     return NGLWidget(structure_trajectory, **kwargs)
    293 
    294 

~/anaconda3/lib/python3.6/site-packages/nglview-1.0a7-py3.6.egg/nglview/widget.py in __init__(self, structure, representations, parameters, **kwargs)
    124         if isinstance(structure, Trajectory):
    125             name = py_utils.get_name(structure, kwargs)
--> 126             self.add_trajectory(structure, name=name)
    127         elif isinstance(structure, (list, tuple)):
    128             trajectories = structure

~/anaconda3/lib/python3.6/site-packages/nglview-1.0a7-py3.6.egg/nglview/widget.py in add_trajectory(self, trajectory, **kwargs)
   1022         setattr(trajectory, 'shown', True)
   1023         self._trajlist.append(trajectory)
-> 1024         self._update_count()
   1025         self._ngl_component_ids.append(trajectory.id)
   1026         self._update_component_auto_completion()

~/anaconda3/lib/python3.6/site-packages/nglview-1.0a7-py3.6.egg/nglview/widget.py in _update_count(self)
    306     def _update_count(self):
    307         self.count = max(
--> 308             traj.n_frames for traj in self._trajlist
    309             if hasattr(traj, 'n_frames'))
    310 

~/anaconda3/lib/python3.6/site-packages/traitlets/traitlets.py in __set__(self, obj, value)
    583             raise TraitError('The "%s" trait is read-only.' % self.name)
    584         else:
--> 585             self.set(obj, value)
    586 
    587     def _validate(self, obj, value):

~/anaconda3/lib/python3.6/site-packages/traitlets/traitlets.py in set(self, obj, value)
    557 
    558     def set(self, obj, value):
--> 559         new_value = self._validate(obj, value)
    560         try:
    561             old_value = obj._trait_values[self.name]

~/anaconda3/lib/python3.6/site-packages/traitlets/traitlets.py in _validate(self, obj, value)
    589             return value
    590         if hasattr(self, 'validate'):
--> 591             value = self.validate(obj, value)
    592         if obj._cross_validation_lock is False:
    593             value = self._cross_validate(obj, value)

~/anaconda3/lib/python3.6/site-packages/traitlets/traitlets.py in validate(self, obj, value)
   1868     def validate(self, obj, value):
   1869         if not isinstance(value, int):
-> 1870             self.error(obj, value)
   1871         return _validate_bounds(self, obj, value)
   1872 

~/anaconda3/lib/python3.6/site-packages/traitlets/traitlets.py in error(self, obj, value)
    623             e = "The '%s' trait must be %s, but a value of %r was specified." \
    624                 % (self.name, self.info(), repr_type(value))
--> 625         raise TraitError(e)
    626 
    627     def get_metadata(self, key, default=None):

TraitError: The 'count' trait of a NGLWidget instance must be an int, but a value of 656694 <class 'numpy.int64'> was specified.
```

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `34643ba655af`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
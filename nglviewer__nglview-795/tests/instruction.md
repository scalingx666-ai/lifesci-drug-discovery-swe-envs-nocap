# Issue

**Title:** ADD (sandbox code) for trajectory smoothing

## Description

Related case: #740 

![smooth](https://user-images.githubusercontent.com/4451957/57004893-edcbb300-6ba0-11e9-82a2-50dfc6368426.gif)

Code example:
```python
import nglview as nv
from nglview.sandbox.interpolate import smooth
import pytraj as pt

traj = pt.datafiles.load_trpcage()[:]
traj.superpose()
traj_smoothed = traj.copy()
traj_smoothed.xyz = smooth(traj_smoothed.xyz, method='savgol_filter', window_length=11, polyorder=3)
traj.translate('x 20')
traj_smoothed3 = traj.copy()
traj_smoothed3.xyz = smooth(traj_smoothed3.xyz)
traj.translate('x 20')

kwargs = {'default_representation': False}
view = nv.NGLWidget()

c0 = view.add_trajectory(nv.PyTrajTrajectory(traj), **kwargs)
c0.add_ball_and_stick('backbone or TRP')

c1 = view.add_trajectory(nv.PyTrajTrajectory(traj_smoothed), **kwargs)
c1.add_ball_and_stick('backbone or TRP')

c3 = view.add_trajectory(nv.PyTrajTrajectory(traj_smoothed3), **kwargs)
c3.add_ball_and_stick('backbone or TRP')

view.control.orient([28.27254663341445,
 0,
 3.409084934332838,
 0,
 0,
 28.477337537559414,
 0,
 0,
 -3.409084934332838,
 0,
 28.27254663341445,
 0,
 -21.208489890749334,
 -0.23829763922190267,
 0,
 1])

view.camera = 'orthographic'
view
```

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3a51ef37c82f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
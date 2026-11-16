# Issue

**Title:** Add support for band structure titles

## Description

Hi Sumo devs,

I'm a physics PhD student at UC Berkeley/Berkeley Lab working with Dr. Sinéad Griffin. Sumo is one of my favorite tools and I use it quite heavily, so I would love to contribute.

This very simple PR adds a "title" feature to band plots,  including the new `--title` flag of `sumo-bandplot` and `title` argument of `SBSPlotter.get_plot` and `SBSPlotter.get_projected_plot`. I've found this extremely helpful when, for example, looking at the changes in the electronic structure as you distort or displace atoms-- it's quite helpful for making high quality GIFs for presentations.

Example:
![image](https://github.com/SMTG-UCL/sumo/assets/11034116/b7cf399e-b881-44a6-b2bc-de6ffc695b05)

Example GIF showing the effect of phonons of different amplitudes on Sr3PbO:
![mode1 3](https://github.com/SMTG-UCL/sumo/assets/11034116/6cc97fce-ae82-4f3b-8fae-756e1e1ef4f3)

I have not implemented titles for the other types of plots (DOS, optics, phonons), but it's quite easy to do and I'll see if I can get around to it. I'm not new to developing Python packages (or scientific software more broadly), but I've always worked solo, so please let me know if you have any feedback or guidelines!

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0f469ef94cc6`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
# Issue

**Title:** Add `**kwargs` to `draw_themed_line`

## Description

Hi @utf and @ajjackson!
This is a tiny update to allow the user to pass `kwargs` to `draw_themed_line`. The main reason is so that we can control `zorder` when importing and using this function, if the band plot is e.g. actually a colourmap, in which case the default `zorder=0` hides the zero line, but bumping it up shows it. 
This is because I'm using `sumo` to add co - DOS plot functionality (like `sumo-bandplot`) to the unfolded bandstructure plotting in [`easyunfold`](https://smtg-ucl.github.io/easyunfold/), so using some of these useful functions! 🙌

Work in progress, but like this:
![image](https://github.com/SMTG-UCL/sumo/assets/51478689/fb9ace3d-51d7-4578-882a-4ff534939bdd)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0f469ef94cc6`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
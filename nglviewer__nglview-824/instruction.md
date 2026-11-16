# Issue

**Title:** ADD sandbox code for fullscreen_mode + REMOVE: spin from player (rarely used?)

## Description

Absolutely a sandbox code 

```
from nglview.sandbox.grid_view import fullscreen_mode

fullscreen_mode(view) # will add a `Fullscreen` button to the player
```

<img width="1023" alt="Screen Shot 2019-06-20 at 1 20 41 AM" src="https://user-images.githubusercontent.com/4451957/59822012-b2747780-92f9-11e9-8be2-aaa8e45e90c8.png">

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0b262e182a85`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
# Issue

**Title:** Add functionality to select backend

## Description

Hi,

Here is my second try at implementing the backend selection feature. I've been quite busy, so that's why it took a bit longer than I wanted to put this pull request. Either way, below is a short summary:
I only modified graph.py, and I tried to change as little as possible.
I use environment variables to check and update backend. I also added a function to check all available backends, and to see the current backend. (That last one maybe is a bit redundant and could be removed). 
Everything seems to work fine, except there is one edge-case/"bug" with the to_graph() functionality of a molecule: if you use this before and after switching to another backend for the same molecule, it will still return the graph of the old backend because of the cache. I would propose to make use of a dictionary structure, where the (standardized) names of the backends serve as keys and the values the graphs. I could implement this quite easily, but ofcourse this would require some tweaks to molecule.py. That's why I waited with implementing this in order to first hear your opinion. Maybe there's a better way? 
Also, I didn't add any tests yes, since I'd like your feedback/opinion first! After that i'll gladly spend some more time to polish everything!

---

Close #68

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d498f6e06390`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
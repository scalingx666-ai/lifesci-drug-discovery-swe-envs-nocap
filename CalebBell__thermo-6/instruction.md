# Issue

**Title:** New function - calculate bubble point temperature + minor edit to chemicals

## Description

Hi Caleb, 

This project is really nice! I found your project just last week or so, and have been playing around with it since. I'm amazed at the work you have here. 

This pull request adds a function that calculates the bubble point temperature given a composition and pressure. In the process, I noticed that the chemicals test failed to initialize temperature for some components and fails. A small tweak fixes the issue, however, I'm not sure if the original placement was intentional. 

I hope this helps. I'm greatly interested in helping out this project where and when I can. 

-Enrique

P.S. Apologies for all the whitespace changes. My editor automatically removes them on saving. I can see about disabling that for future submissions.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3069c0e51558`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
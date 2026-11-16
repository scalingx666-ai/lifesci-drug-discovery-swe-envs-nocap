# Issue

**Title:** Fix colour parsing for BS + DOS plots

## Description

I noticed that when plotting the DOS alongside the band structure with `sumo`, the DOS colours changed from what they were with `sumo-dosplot` (which can ofc be a bit annoying when putting these figures in SI for example, as colours aren't consistent), unless you explicitly pointed to the `orbital_colours.conf` file or used your own one.
<img width="801" alt="image" src="https://user-images.githubusercontent.com/51478689/119374715-cf6a1000-bcb1-11eb-90ad-7ccd6ec5c831.png">
![image](https://user-images.githubusercontent.com/51478689/119374848-017b7200-bcb2-11eb-917c-30e5291b750f.png)


From a bit of digging, I found that this came from a small typo in `bandplot.py`, fixed now! (This line now matches that in `dosplot.py`)

<img width="1147" alt="image" src="https://user-images.githubusercontent.com/51478689/119374878-093b1680-bcb2-11eb-8fa1-ef52dbfcbfd7.png">

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `da6f03812b4c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
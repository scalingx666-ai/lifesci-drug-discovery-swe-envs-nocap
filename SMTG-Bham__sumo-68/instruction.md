# Issue

**Title:** Draw Fermi level in the panels of bands and DOS

## Description

Hi, Dr. Ganose( @utf ) and Dr. Jakson @ajjackson 

Firstly, Thank you very much for your code.

Secondly, I noticed that the Fermi level is only drawn if the Fermi energy is not shifted to zero. However, I think it's better to show it clearly in both bands and DOS panels no matter shift or not.
Showing the Fermi level clearly is important for all the materials (although it's only my personal opinion). For example, in insulators, it can easily help tell the direct bandgap or indirect bandgap. More importantly, for the topological semimetals and topological insulators that show singular points around the Fermi level, this line can help to know whether they are exactly located on the Fermi level. Hence, I made minor revisions to show the Fermi level lines on bands and DOS. Because in the dos_plotter.py, there is a possibility that the legend is on top of the Fermi level, so I used a very light black (alpha = 0.3) to show the Fermi level. In addition, the 'dashed' style has been used in bands plotter (for the spin down channel), hence I used the 'dashdot' style to show the Fermi level. 
This is just a personal opinion, but you may have a consideration of it. Thank you very much!

FYI: A sample figure with the Fermi level lines shown
![image](https://user-images.githubusercontent.com/16239703/61643016-f97cd080-acdc-11e9-94da-7edee6d6cbc1.png)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ac6b2de5020b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
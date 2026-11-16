# Issue

**Title:** Adding iSIM as a trackable value during training

## Description

Sorry it took me so long to get to this. 
I have made the changes needed in the REINVENT code to track the iSIM average similarity across each training step, and add this value to the tensorboard output. 

Below is a list of the changes I made: 
1. In learning.py I have imported iSIM, computed binary RDKIT fingerprints from the smilies array, and computed isim from the generated fingerprints. I then added isim as a variable to the report_data dictionary. 
2. In data.py I have added the isim variable to RLReportData.
3. In tensorboard.py I have added iSIM:Average Similarity to the report as a scalar per each step.

I want to mention that I started with the absolute barebones steps for this implementation. I want to make sure this is what you all are looking for. 

Below are other changes I can make: 
1. I have coded this by importing iSIM functions from the installable package. This now makes the iSIM package a dependency for REINVENT. If this is not what you all want I can either hard code the iSIM functions I used into the script, or add some variable so that iSIM is only imported if the user sets this to True. 
2. For the fingerprint generation I am currently computing binary fingerprints from RDKIT. We support different fingerprint types in this function, I can also make this optional for the user
3. With iSIM, we can compute different types of average pairwise similarities. In this current implementation I have used Tanimoto. I can also make it optional for the user to choose the other similarity types we support. 

Please let me know if this was not what you were looking for, or if you are interested in any of the above additions. Also, let me know if there was a place in the REINVENT code that I missed adding the iSIM variable. With the test code I ran, this successfully adds the iSIM value per step in the tensorboard event file. 

Best, 
Kate Huddleston

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `308d3ff9c6f0`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
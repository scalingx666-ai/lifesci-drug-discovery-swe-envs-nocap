# Issue

**Title:** Molden exporting enabled

## Description

In this PR, as requested in issue #251, I have enabled capability to export data from QUICK into molden format. Users can put `EXPORT=MOLDEN` in input file and this would result in input_name.molden file in the working directory. Ive followed this article: https://www.theochem.ru.nl/molden/molden_format.html for molden format, however, molden and other visualization software Ive tried dont read SCF/geometry convergence data. Interestingly, other QM codes (eg. MOLCAS, PSI4) do not write these sections into molden files. Not sure why.. Below are some orbital images generated using QUICK's molden files and JMOL. 

<img width="955" alt="Screen Shot 2022-07-22 at 11 00 12 AM" src="https://user-images.githubusercontent.com/46697377/180480511-b828e234-9d7e-4553-9d9c-47b703ea5a58.png">
<img width="904" alt="Screen Shot 2022-07-22 at 11 00 33 AM" src="https://user-images.githubusercontent.com/46697377/180480515-7c4ace4d-a210-4075-af57-ee1fafbcb9c2.png">
<img width="696" alt="Screen Shot 2022-07-22 at 11 02 55 AM" src="https://user-images.githubusercontent.com/46697377/180480518-84c0ebbc-a748-4f70-a137-70878a9e976e.png">
<img width="736" alt="Screen Shot 2022-07-22 at 11 03 09 AM" src="https://user-images.githubusercontent.com/46697377/180480520-58471960-fb2f-41cb-baf4-84c24db41ec1.png">

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d89bbaf77133`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
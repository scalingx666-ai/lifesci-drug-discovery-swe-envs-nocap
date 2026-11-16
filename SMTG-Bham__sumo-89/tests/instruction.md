# Issue

**Title:** Spin-Polarisation Selection Option

## Description

I've added a 'spin' option to the CLI interface for _sumo-dosplot_ and _sumo-bandplot_, including _sumo-bandplot_ projected BS. The syntax is explained in the docstrings and help output: "spin (:obj:`str`, optional): Plot a spin-polarised band structure, "up" for spin up only, "down" for spin down only. Defaults to ``None``."  
I've checked that it works as it should.  
Examples:  
Spin-polarised DOS (Before Changes)  
![spinpoldosorig](https://user-images.githubusercontent.com/51478689/69919592-76336e80-1476-11ea-8413-c40fea96ff09.png)  
Spin-polarised DOS, Spin Up Only (After Changes)  
![spinpoldownewspindownonly](https://user-images.githubusercontent.com/51478689/69919590-759ad800-1476-11ea-975e-a7d3f138d4b8.png)  
Spin-polarised DOS, Spin Down Only (After Changes)  
![spinpoldosnewspinuponly](https://user-images.githubusercontent.com/51478689/69919591-76336e80-1476-11ea-903b-c9763ac63fec.png)  

Spin-Polarised BS (Before Changes)  
![spinpolbandorig](https://user-images.githubusercontent.com/51478689/69919597-76cc0500-1476-11ea-968f-a16902c9fc21.png)  
Spin-Polarised BS, Spin Down Only (After Changes)  
![spinpolbandnewspindownonly](https://user-images.githubusercontent.com/51478689/69919595-76336e80-1476-11ea-993e-bb9ca956d11b.png)  
Spin-Polarised BS, Spin Up Only (After Changes)  
![spinpolbandnewspinuponly](https://user-images.githubusercontent.com/51478689/69919596-76cc0500-1476-11ea-879d-6619bdb7609c.png)  
Spin-Polarised BS with Projections (Spin Down Only)(After Changes)  
![spinpolprojbandnewspindownonly](https://user-images.githubusercontent.com/51478689/69919593-76336e80-1476-11ea-8fab-aee83de2ae2b.png)  
Spin-Polarised BS with Projections (Spin Up Only)(After Changes)  
![spinpolprojbandnewspinuponly](https://user-images.githubusercontent.com/51478689/69919594-76336e80-1476-11ea-947b-0d4ab070b23a.png)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `488d27f7d068`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
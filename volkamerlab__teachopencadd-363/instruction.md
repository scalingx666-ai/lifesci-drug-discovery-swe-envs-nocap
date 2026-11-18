# Issue

**Title:** T020: update deprecated code fix broken ci

## Description

## Description
T020 fails with cryptic message in CI under MacOS:
```
UserWarning: Reload offsets from trajectory
 ctime or size or n_atoms did not match
  warnings.warn("Reload offsets from trajectory\n "
```
Try to fix this by rerunning on local MacOS & fix warnings etc. along the way.

**Note**: I recommend merging  first, only then this PR (as this PR branches off `t019-exclude-windows-from-ci`).

## Todos
- [x] Fix code with deprecation warnings from MDAnalysis
  - Instance 1  
       ```
       rmsd_analysis = rms.RMSD(...)
       rmsd_analysis.run()
       rmsd_analysis.rmsd → rmsd_analysis.results.rmsd
       ```
  - Instance 2  
       ```
       pairwise_rmsd = diffusionmap.DistanceMatrix(...)
       pairwise_rmsd.run()
       pairwise_rmsd.dist_matrix → pairwise_rmsd.results.dist_matrix
       ```
  - Instance 3  
       ```
       hbonds = HBA(...)
       hbonds.run()
       hbonds.hbonds → hbonds.results.hbonds
       ```
- [x] Rerun notebooks manually (take care of 3D viewer views)
- [x] Update `xtc_offsets.npz` file and add `xtc_offsets.lock` (from manual rerun), see notes in [docs](https://docs.mdanalysis.org/stable/documentation_pages/coordinates/XDR.html#MDAnalysis.coordinates.XDR.XDRBaseReader) --> CI fail remains
- [x] Remove both files, see commit  --> CI fail gone? yes, it seems so ([passing CI](https://github.com/volkamerlab/teachopencadd/actions/runs/5050485558/jobs/9061254027?pr=363))
- [x] Run CI only for T020 (to be faster) & revert back those changes from commit 


## Status
- [x] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2f6a5e0b558e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
# Issue

**Title:** Fix band stats k-point labels

## Description

## Summary

This PR fixes a long-standing (since 2022) bug in `sumo-bandstats` in that the labels for the effective masses don't show correctly. E.g., this is the output for the band stats in `test/data/Cs2SnI6/bandstructure`:
```
  m_h: -0.641 | band 35 | [0.00, 0.00, 0.00] (\Gamma) -> [0.00, 0.00, 0.00] (\Gamma)
  m_h: -0.516 | band 35 | [0.00, 0.00, 0.00] (\Gamma) -> [0.00, 0.00, 0.00] (\Gamma)
  m_h: -0.641 | band 36 | [0.00, 0.00, 0.00] (\Gamma) -> [0.00, 0.00, 0.00] (\Gamma)
  m_h: -0.516 | band 36 | [0.00, 0.00, 0.00] (\Gamma) -> [0.00, 0.00, 0.00] (\Gamma)
  m_h: -1.234 | band 37 | [0.00, 0.00, 0.00] (\Gamma) -> [0.00, 0.00, 0.00] (\Gamma)
  m_h: -15.158 | band 37 | [0.00, 0.00, 0.00] (\Gamma) -> [0.00, 0.00, 0.00] (\Gamma)
```
Obviously the effective masses are not in the Gamma -> Gamma direction (which doesn't make sense). The output for the new version is:
```
  m_h: -0.641 | band 35 | [0.00, 0.00, 0.00] (\Gamma) -> [0.50, 0.50, 0.50] (L)
  m_h: -0.516 | band 35 | [0.00, 0.00, 0.00] (\Gamma) -> [0.50, 0.00, 0.50] (X)
  m_h: -0.641 | band 36 | [0.00, 0.00, 0.00] (\Gamma) -> [0.50, 0.50, 0.50] (L)
  m_h: -0.516 | band 36 | [0.00, 0.00, 0.00] (\Gamma) -> [0.50, 0.00, 0.50] (X)
  m_h: -1.234 | band 37 | [0.00, 0.00, 0.00] (\Gamma) -> [0.50, 0.50, 0.50] (L)
  m_h: -15.158 | band 37 | [0.00, 0.00, 0.00] (\Gamma) -> [0.50, 0.00, 0.50] (X)
```

## Details

This bug was introduced when trying to fix another bug (), specifically that the k-point indices listed in `sumo-bandstats` were wrong.

This all comes from the fact that the pymatgen logic for extracting branches in the band structure requires duplicating the high-symmetry points. To avoid wasting compute resources on these extra points, sumo-bandplot/bandstats adds this points dynamically rather than including them in the DFT calculation. However, this means sumo-bandstats reports the wrong indices for the VBM and CBM with respect to the band structure calculation. The previous PR tried to fix this issue by removing the branches for `sumo-bandstats` but this then led to the labels being missing.

The fix in this PR is to:
1. Revert the change in  and instead always keep the branches (to get the correct labels).
2. Calculate a mapping for the k-point indices from the branched band structure to the original band structure indices. Use this mapping when logging the band stats information.

## Other fixes

I also added a quick fix the VASP bug where it sometimes puts the Fermi level in the valence or conduction bands when using ISMEAR = -5. I already added a workaround for this in pymatgen (specifically `vr.get_band_structure(line_mode=True, efermi="smart")`) but it currently isn't used in sumo.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9ec6740c423f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
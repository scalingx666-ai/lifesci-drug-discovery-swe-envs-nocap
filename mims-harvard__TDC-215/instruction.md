# Issue

**Title:** Add Blood-Brain Barrier Database (B3DB) to TDC

## Description

Based on discussion in  adding the Blood-Brain Barrier Database (B3DB) to TDC. Currently *not* adding B3DB to the ADMET benchmark group, but this could be added later (@kexinhuang12345, please see ).

## Dataset Description

The Blood-Brain-Barrier Dataset (B3DB) is a curated resource of 7,807 small molecules classified as either BBB permeable (BBB+) or BBB non-permeable (BBB-), with 4,956 BBB+ and 2,851 BBB- molecules originally included. BBB permeability is measured by the logarithm of the brain-plasma concentration ratio:

$$\log{BB} = \log{\frac{C_{brain}}{C_{blood}}}$$

Numerical $\log{BB}$ data was originally included for 1,058 of the 7,807 molecules in the dataset.

## Data Processing

After removing duplicates and `NA` IUPAC identifiers, there is classification data for 6,167 molecules and regression data for 942 molecules. Data processing script available at: https://gist.github.com/ayushnoori/af42cc651856f347614d0bd2a8fe7def

## Data Description

We add two new datasets:
* `b3db_classification`: Binary permeability label for all 6,167 small molecules, where the $\log{BB}$ ratio is binarized using $\log{BB} > 0 =$ BBB+ (*i.e.*, 1) and $\log{BB} < 0 =$ BBB- (*i.e.*, 0).
* `b3db_regression`: Numerical $\log{BB}$ data for 942 small molecules.

## Reference

Meng, F., Xi, Y., Huang, J. & Ayers, P. W. [A curated diverse molecular database of blood-brain barrier permeability with chemical descriptors.](https://www.nature.com/articles/s41597-021-01069-5) *Sci Data* **8**, 289 (2021).

DOI: [10.1038/s41597-021-01069-5](https://doi.org/10.1038/s41597-021-01069-5)

GitHub: https://github.com/theochem/B3DB

Harvard DataVerse: [https://dataverse.harvard.edu/dataset.xhtml?persistentId=doi:10.7910/DVN/1RVMJ0](https://dataverse.harvard.edu/dataset.xhtml?persistentId=doi:10.7910/DVN/1RVMJ0)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `15809f26ef11`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
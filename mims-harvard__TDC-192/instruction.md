# Issue

**Title:** Added Nine New Datasets; Fixed bug; Updated CONTRIBUTE.md

## Description

# Dataset Description
These are nine high-quality high-throughput screening (HTS) datasets from [1]. These datasets were curated from HTS data at the PubChem database [2]. Typically, HTS categorizes small molecules into hit, inactive, or unspecified against a certain therapeutic target. However, a compound may be falsely classified as a hit due to experimental artifacts such as optical interference. Moreover, because the screening is performed without duplicates, and the cutoff is often set loose to minimize the false negative rates, the results from the primary screens often contain high false positive rates [3].  Hence the result from the primary screen is only used as the first iteration to reduce the compound library to a smaller set of further confirmatory tests.  

Here each dataset is carefully collated through confirmation screens to validate active compounds. The curation process is documented in [1]. Each dataset is identified by the PubChem Assay ID (AID).

**Features of the Datasets:**
1. At least 150 confirmed active compounds present
2. Diverse target classes
3. Realistic (large number and highly imbalanced label)

# Task description
Binary classification. Given a compound SMILES string, predict its activity against a diverse set of targets.

# Dataset Statistics 
Protein Target Class | PubChem AID | Protein Target | Total # of Molecules| # of Active Molecules
|----------------------|-----------------|---------------| ----------------------| ------------------------
GPCR | 435008 | Orexin1 Receptor | 218,158 | 233
GPCR | 1798 | M1 Muscarinic Receptor Agonists | 61,833 | 187
GPCR | 435034 | M1 Muscarinic Receptor Antagonists | 61,756 | 362
Ion Channel | 1843 | Potassium Ion Channel Kir2.1 | 301,493 | 172
Ion Channel | 2258 | KCNQ2 Potassium Channel | 302,405 | 213
Ion Channel | 463087 | Cav3 T-type Calcium Channels | 100,875 | 703
Transporter | 488997 | Choline Transporter |302,306 | 252
Kinase | 2689 | Serine/Threonine Kinase 33 | 319,792 | 172
Enzyme | 485290 | Tyrosyl-DNA Phosphodiesterase | 341,365 | 281


# Data Split Methods
1. Random
2. Scaffold

# References 
[1] [Butkiewicz, Mariusz, et al. "Benchmarking ligand-based virtual High-Throughput Screening with the PubChem database." Molecules 18.1 (2013): 735-756.](https://www.mdpi.com/1420-3049/18/1/735)
[2] [Kim, Sunghwan, et al. "PubChem 2019 update: improved access to chemical data." Nucleic acids research 47.D1 (2019): D1102-D1109.](https://academic.oup.com/nar/article/47/D1/D1102/5146201)
[3] [Butkiewicz, Mariusz, et al. "High-throughput screening assay datasets from the pubchem database." Chemical informatics (Wilmington, Del.) 3.1 (2017).](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC5962024/)

# Examples
```
from tdc.single_pred import HTS
# Orexin1 Receptor
data = HTS(name = 'orexin1_receptor_butkiewicz')
df = data.get_data()
splits = data.get_split()

# M1 Muscarinic Receptor Agonists
data = HTS(name = 'm1_muscarinic_receptor_agonists_butkiewicz')
df = data.get_data()
splits = data.get_split()

# M1 Muscarinic Receptor Antagonists
data = HTS(name = 'm1_muscarinic_receptor_antagonists_butkiewicz')
df = data.get_data()
splits = data.get_split()

# Potassium Ion Channel Kir2.1 
data = HTS(name = 'potassium_ion_channel_kir2.1_butkiewicz')
df = data.get_data()
splits = data.get_split()

# KCNQ2 Potassium Channel
data = HTS(name = 'kcnq2_potassium_channel_butkiewicz')
df = data.get_data()
splits = data.get_split()

# Cav3 T-type Calcium Channels
data = HTS(name = 'cav3_t-type_calcium_channels_butkiewicz')
df = data.get_data()
splits = data.get_split()

# Choline Transporter
data = HTS(name = 'choline_transporter_butkiewicz')
df = data.get_data()
splits = data.get_split()

# Serine/Threonine Kinase 33
data = HTS(name = 'serine_threonine_kinase_33_butkiewicz')
df = data.get_data()
splits = data.get_split()

# Tyrosyl-DNA Phosphodiesterase
data = HTS(name = 'tyrosyl-dna_phosphodiesterase_butkiewicz')
df = data.get_data()
splits = data.get_split()
```

# Other Updates in This Pull Request
1. Fix bug: file utils/split.py line 152 throw error `Name 'print_sys' is not defined` when a SMILES cannot be converted into mol by RdKit.
**Solution**
added `from .misc import print_sys` in the front of the file.
2. Some instructions about dataset uploading in the CONTRIBUTE.md are either confusing or misleading. Updated those for clarity.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `7045539c78d9`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
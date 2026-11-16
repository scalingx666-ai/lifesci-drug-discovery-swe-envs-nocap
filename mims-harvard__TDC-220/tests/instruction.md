# Issue

**Title:** Conda environment setup for TDC. Also installs cellxgene-census

## Description

To install tdc, simply run

`conda env create -f environment.yml`

Test below
...

Successfully installed PyTDC-0.4.1 aiobotocore-2.11.2 aiohttp-3.9.3 aioitertools-0.11.0 aiosignal-1.3.1 anndata-0.10.5.post1 array-api-compat-1.4.1 async-timeout-4.0.3 attrs-23.2.0 botocore-1.34.34 cellxgene-census-1.10.2 exceptiongroup-1.2.0 frozenlist-1.4.1 get-annotations-0.1.2 h5py-3.10.0 jmespath-1.0.1 llvmlite-0.42.0 multidict-6.0.5 natsort-8.4.0 networkx-3.2.1 numba-0.59.0 pyarrow-12.0.1 pyarrow-hotfix-0.6 pynndescent-0.5.11 rdkit-pypi-2022.9.5 s3fs-2024.2.0 scanpy-1.9.8 seaborn-0.13.2 session-info-1.0.0 somacore-1.0.7 stdlib_list-0.10.0 tiledb-0.25.0 tiledbsoma-1.7.2 umap-learn-0.5.5 urllib3-1.26.18 wrapt-1.16.0 yarl-1.9.4

done

 To activate this environment, use

     $ conda activate tdc-conda-env

 To deactivate an active environment, use
     $ conda deactivate

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `10865f638a77`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
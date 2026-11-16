# Issue

**Title:** Fix a problem with generating conformers of highly strained chiral centers

## Description

The check that the embedding code does to make sure that a chiral center is contained inside the volume formed by its four neighbors is overly strict for highly strained chiral centers like those in this molecule:
<img width="450" height="450" alt="image" src="https://github.com/user-attachments/assets/b7a7f920-ae49-4b49-97ee-3b9d63775488" />
here's the 3D structure from the COD:
<img width="337" height="290" alt="image" src="https://github.com/user-attachments/assets/2a948676-4ff2-4fc2-8e78-467daf1d4067" />

This PR relaxes the chiral-center-in-volume check a little bit in order to allow structures like this to be embedded.

Also:

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `07b2920df590`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
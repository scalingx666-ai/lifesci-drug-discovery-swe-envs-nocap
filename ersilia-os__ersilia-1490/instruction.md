# Issue

**Title:** Use DataFrame class to serialize h5 and csv

## Description

The PR has resorted to use the `DataFrame` class in the `ersilia/io/output.py` module to serialize to both CSV and HDF5 formats. Since the user only needs to pass the data and column fields to create a `DataFrame` object and these are readily available from the models built with the Ersilia Pack template, this object can be easily created bypassing the `to_dataframe` method in the `GenericOutputAdaptor` class.

Also note that this modification is only introduced in the `adapt_when_using_fastapi` method, therefore all legacy models should continue to work as is.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0c732529e38f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
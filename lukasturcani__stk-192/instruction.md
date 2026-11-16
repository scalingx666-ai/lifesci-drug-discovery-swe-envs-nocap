# Issue

**Title:** put() should update all matching entries.

## Description

At the moment, calling `put()` would add a new record into the database.  For example, running

```python

db = stk.ValueMongoDb(...)
db.put(molecule, 1)
db.put(molecule, 2)
```

would mean that the MongoDB collection has 2 entries, one which says the molecule has a value of  `1` and one which says the molecule has a value of `2`.

The desired behavior is to find any records in the database which have matching `MoleculeKey` values, and update those records, if they exist, instead of adding new ones. New ones should only be added if no matching record already exists, hence the use of `upsert=True`. Therefore, running the above code should mean that there is only 1 entry in the MongoDB collection.

There is a test for checking that the database was successfully updated, rather than having a new entry added, coming in a later PR.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9c61320c4ed2`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
# Issue

**Title:** Dump database

## Description

Related Issues: #277 
Requested Reviewers: @andrewtarzia 
*Note for Reviewers: If you accept the review request add a :+1: to this post*

This PR adds a new test, `test_dump_molecule_structures()`, which 
is responsible for dumping the molecular structures to files and
placing them into a MongoDB database. Previously the file dumping
was done in the `test_get_atoms()` test, but I think having a 
separate test for this is better, because it keeps better to the single
responsibility principle. 

The PR also updates the CI to dump the MongoDB database after
the tests have been run, so that it can be downloaded and viewed
locally, for example with `stk-vis`. To help viewing with `stk-vis`
the file `tests/mongo-config.json` has been added. It can be 
loaded into `stk-vis` and configures it so that the developer does
not have to manually change the database name or the molecule
key name.

The PR also adds a new utility script `drop_test_database.py` which
just drops the databases which running the tests creates. This script
is meant to be run manually if a developer wants to remove the 
databases for some reason.

Finally, the PR also removes all uses of the MongoDB action with a 
MongoDB service container in the CI. This just seems more idiomatic
to me.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6c5619200f71`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
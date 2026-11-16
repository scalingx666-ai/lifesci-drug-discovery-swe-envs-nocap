# Issue

**Title:** Migration of molecule storage away from opaque msgpack columns

## Description

## Description
<!-- Thank you for your contribution! -->
<!-- Provide a brief description of the PR's purpose here. -->

Previously, molecules had some fields stored as MsgpackExt columns. This would make it hard to do some future queries or molecule management. This PR moves those columns into postgres-native types (`ARRAY` and `JSON`) which will make future molecule handling easier. This should be backwards compatible with current QCPortal versions, as it only affects how molecules are stored, not sent through the API.

Our instances have a lot of molecules (100M+), so this takes a **very very long time** (days) if done solely through the `upgrade-db` (alembic) migration path. It is possible to use an intermediate commit, upgrade the database to that, and then use the `server_admin/migrate_molecule_msgpack.py` script. This will be faster (multi-process), and allows for migration while the qcfractal instance is running. Then you can upgrade to the final version of QCFractal as necessary. If you need to know more, contact me.

## WARNING

Make sure your database is backed up before performing this migration! I've tested it on various instances and it appears safe, but this is a very sensitive area, and reverting to a previous state is not possible without a backup.

## Status
- [X] Code base linted
- [X] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ade2bc557839`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
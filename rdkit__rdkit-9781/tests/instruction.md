# Issue

**Title:** Fixes full backend crash in `mol_adjust_query_properties()` on malformed JSON

## Description

`mol_adjust_query_properties()` with malformed JSON options terminates the PostgreSQL backend:

```sql
select mol_adjust_query_properties('Cc1ccccc1'::mol, '{"adjustDegree":false');
-- WARNING:  adjustQueryProperties: Invalid argument 'params' ignored
-- server closed the connection unexpectedly
```

```
terminate called after throwing an instance of 'boost::wrapexcept<boost::property_tree::json_parser::json_parser_error>'
LOG:  client backend (PID 111) was terminated by signal 6: Aborted
LOG:  all server processes terminated; reinitializing
```

The PostgreSQL then restarts every backend and runs crash recovery, so all sessions are dropped.

`MolAdjustQueryProperties` (`Code/PgSQL/rdkit/adapter.cpp`) parses the options twice. The first parse (`parseAdjustQueryParametersFromJSON`) is inside a `try` and only warns. The second parse, which reads `setGenericQueryFromProperties`, called `read_json` outside the `try`, so the parser exception escaped the `extern "C"` function and reached `std::terminate`.

This allows **any** db user to crash the PostgreSQL server (and all the running transactions) by providing malformed JSON.

## fix

Move the second parse into the existing `try` block.
Malformed JSON now produces the existing WARNING and the default parameters.
Valid input behaves the same as before.

## test

Added a malformed-JSON case to `sql/rdkit-91.sql` / `expected/rdkit-91.out`.

Ran `pgsql_regress.sh` on PostgreSQL 16 (Ubuntu 24.04, arm64)
- with the fix: all 15 tests pass
- without the fix: the new statement aborts the backend (`signal 6`) and all 15 tests fail

## disclaimer

Claude Opus 5.5 was used in bug research, validation and fix proposal with human review where needed

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d37b89a6d7eb`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
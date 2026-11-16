# Issue

**Title:** Fix binary receive functions in PostgreSQL cartridge

## Description

#### Reference Issue
N/A

#### What does this implement/fix? Explain your changes.
PostgreSQL's `ReceiveFunctionCall` passes a `StringInfo` buffer (`StringInfoData *`) as `internal` argument `0` to `typereceive` functions (`mol_recv(internal)`, `qmol_recv(internal)`, `xqmol_recv(internal)`, and `reaction_recv(internal)`), rather than a `bytea *` datum.

Previously, `mol_recv`, `xqmol_recv`, and `reaction_recv` in `Code/PgSQL/rdkit/rdkit_io.c` read argument `0` via `PG_GETARG_BYTEA_P(0)`, causing `pg_detoast_datum` to misinterpret the first 4 bytes of `StringInfoData` (its `char *data` pointer) as a varlena header. During binary input operations such as `COPY ... FROM ... WITH (FORMAT binary)` or logical replication with `binary = true`, this either crashed the PostgreSQL backend with `SIGSEGV` or failed with `ERROR: problem generating ... from blob data`.

This PR updates `mol_recv`, `xqmol_recv`, and `reaction_recv` to extract the payload from the `StringInfo` buffer using `PG_GETARG_POINTER(0)` and `pq_getmsgbytes(buf, buf->len - buf->cursor)`, and adds a `binary_io` `pg_regress` test covering binary `COPY` round-trips (including `NULL` values) for `mol`, `qmol`, `xqmol`, and `reaction`.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `12b901c741f6`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
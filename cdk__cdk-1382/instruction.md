# Issue

**Title:** Remove unsynchronised shared state from descriptors

## Description

## Summary

Several descriptors keep state that is shared between instances or threads without synchronisation. This PR makes
that state immutable and initialised with the class, an instance field, or local to one calculation. The descriptor
results do not change.

## Problems and changes

- **KierHallSmartsDescriptor, AminoAcidCountDescriptor, RDFProtonDescriptor_G3R/_GDR/_GHR**: the descriptor names
  were kept in a static array that every constructor replaced with a new, empty array before filling it. If an
  instance is created while another one is used, for example with one descriptor instance per thread,
  `getDescriptorNames()` can return `null` names. KierHallSmartsDescriptor now builds its names once in a static
  initialiser; the others keep them in an instance `final` field.
- **APolDescriptor, BPolDescriptor**: the static table of atomic polarisabilities was filled in the constructor.
  It is now a `static final` array, like the TPSA and RDBE tables (#1362). The values are unchanged.
- **ChiPathDescriptor, ChiChainDescriptor, ChiClusterDescriptor, ChiPathClusterDescriptor**: the `SmilesParser` for
  the query paths was created lazily in a field during `calculate`, so all calculations of an instance shared one
  parser. Concurrent use therefore relied on `SmilesParser` being thread-safe, which is not documented. The parser
  is now created for every calculation, with the builder of the given molecule. No failure has been observed; this
  removes shared mutable state at a small cost compared to the Chi calculation.

## Testing

No new tests, because these races depend on timing (as for #1362). All descriptor tests of cdk-qsaratomic,
cdk-qsarmolecular and cdk-qsarprotein pass unchanged.

## Note

The proton RDF descriptors also cache molecule-specific state in instance fields, so one instance must still not be
shared between threads. This PR makes one instance per thread safe for them.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d12b2fc99198`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
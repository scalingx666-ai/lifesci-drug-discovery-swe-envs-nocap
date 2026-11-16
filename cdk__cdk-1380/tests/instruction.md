# Issue

**Title:** Make AtomTypeFactory.getInstance thread-safe

## Description

## Summary

`AtomTypeFactory.getInstance(String, IChemObjectBuilder)` is not thread-safe. Concurrent first calls can read the
same data file several times, return different factory instances, or return `null`.

## Problem

`getInstance` created its static `Hashtable` lazily without synchronisation and looked up and created a factory in
two separate steps:

- Two threads can create two tables, and one replaces the other. A thread that put its factory into the first table
  and then reads from the second one gets `null`, so the caller fails with a `NullPointerException`.
- `containsKey` and `put` are not atomic together, so several threads parse the same data file and receive
  different `AtomTypeFactory` instances.

`CDKAtomTypeMatcher.getInstance` serialises its own calls, but `AtomTypeModel` (used by `Aromaticity.cdkLegacy()` /
`ElectronDonation.cdk()`), `VABCVolume`, `LonePairElectronChecker`, `CDKHydrogenAdder` and others call
`getInstance` directly, e.g. when descriptors are calculated in parallel.

## Changes

- The cache is a `static final ConcurrentHashMap`. `computeIfAbsent` creates every factory exactly once; concurrent
  callers wait for it and never get `null`.
- An existing factory is looked up with `get` first. On Java 8, `computeIfAbsent` locks even for an existing key,
  and `getInstance` is called often: `AtomTypeModel` calls it for every saturated ring carbon.
- The Javadoc states the contract: thread-safe, each data file is read once, and the same instance is returned per
  data file. Creating a factory must not call `getInstance` (it runs inside `computeIfAbsent`); it currently does not.

## Testing

New test `AtomTypeFactoryTest#testGetInstance_String_IChemObjectBuilder_concurrent`: 32 threads call `getInstance`
at the same time for a data file that is not cached yet, and all must get the same non-null factory. It failed in
3 of 3 runs without this change (different instances) and passes with it. The existing tests pass.

## Not changed

Some classes cache the factory in a lazily set static field (`VABCVolume`, `LonePairElectronChecker`, legacy and
structgen classes). Now that `getInstance` is thread-safe, a racy write there only leads to another lookup that
returns the same factory, so they are left unchanged.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6341aa6324a1`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
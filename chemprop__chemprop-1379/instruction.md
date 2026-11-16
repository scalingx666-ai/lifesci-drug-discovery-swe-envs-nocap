# Issue

**Title:** Fix dynamic graph sizes in message passing exports

## Description

## Bug report

Addresses the dynamic graph-size portion of #1335.

Message-passing layers allocate scatter-reduction outputs with `len(bmg.V)`. During `torch.export`, that Python length is specialized to the number of atoms in the export example. Running the exported model on a molecular graph with a different atom count then fails with an out-of-bounds scatter or a dynamic-shape constraint violation.

This change uses the symbolic tensor dimension `bmg.V.shape[0]` for those allocations. The same specialization was present in the shared bond/atom mixins and in both standard and Mol-Atom-Bond final aggregation paths, so all four paths are updated consistently.

`MeanAggregation` is intentionally unchanged, following the performance concern discussed in #1335.

## Example

The regression test exports each message-passing implementation using a three-atom chain and executes the exported program using a five-atom chain. Before this patch, export rejects the atom dimension as specialized to `3`; with this patch, the exported and eager outputs match for:

- `AtomMessagePassing`
- `BondMessagePassing`
- `MABAtomMessagePassing`
- `MABBondMessagePassing`

A separate end-to-end check through ONNX Runtime, using `BondMessagePassing` and `SumAggregation`, changed from an out-of-bounds `ScatterElements` failure to successful inference with a maximum PyTorch/ONNX absolute difference of `4.47e-08`.

## Questions

None. This patch is limited to preserving dynamic graph dimensions and adds no public API, checkpoint, or user-facing behavior changes.

## Checklist

- [x] `black --check`, `isort --check-only`, and `flake8` pass on all changed files
- [x] Dynamic export regression test passes on PyTorch 2.7.0 and 2.13.0
- [x] 128 related unit and integration tests pass on PyTorch 2.7.0
- [x] Appropriate unit tests added

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b83c7d107794`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
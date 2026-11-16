# Issue

**Title:** Report atoms without a defined valence as a descriptor error

## Description

## Summary

The Chi descriptors and `AtomValenceDescriptor` throw a `NullPointerException` for atoms that have no valence in
`AtomValenceTool`. This PR reports such atoms as a regular descriptor error instead.

## Problem

`AtomValenceTool.getValence` returns `valencesTable.get(symbol)` as an `int`. The table covers 47 elements (main
group, noble gases, Hg, Cu, Mn, Co). For other elements (e.g. Fe, Zn, Ni, Pd, Pt, Ag, Au) and for pseudo atoms
(e.g. `*` or R groups), unboxing `null` throws a `NullPointerException`. It escapes `calculate()` of
`ChiPathDescriptor`, `ChiChainDescriptor`, `ChiClusterDescriptor`, `ChiPathClusterDescriptor` (via `ChiIndexUtils`)
and `AtomValenceDescriptor`, although descriptors report failures through `DescriptorValue#getException()`. For
example, `DescriptorEngine.process` does not catch exceptions from `calculate`, so it stops processing the
molecule. This has been known since bug 3023326 (test cases with Pt added in f32e9a27a1).

## Changes

- New `AtomValenceTool.hasValence(IAtom)`: whether a valence is defined for an atom.
- `ChiIndexUtils.evalValenceIndex` throws a `CDKException` that names the element or the pseudo atom, e.g.
  `No valence defined for element Pt` or `No valence defined for pseudo atom *`. The Chi descriptors already catch
  it and return NaN values with the exception.
- `AtomValenceDescriptor.calculate` returns a `DescriptorValue` with this exception and the usual integer
  placeholder (`(int) Double.NaN`, as in other descriptors) instead of throwing.
- `ChiChainDescriptor`, `ChiClusterDescriptor` and `ChiPathClusterDescriptor` labelled errors of the valence index
  calculation as substructure search errors; they are now labelled as valence index errors.

Valences for further elements are not added; this PR only makes the existing limitation a proper error.

## Testing

- `AtomValenceToolTest#hasValence`: C has a valence; Pt and a pseudo atom have none.
- `AtomValenceDescriptorTest`: exact error messages for `Cl[Pt]Cl` and `*CCO`.
- The four Chi descriptor tests for the Pt complex (bug 3023326) previously expected the `NullPointerException`;
  they now expect an error naming Pt and NaN values. `ChiPathDescriptorTest#testPseudoAtom` covers `*CCO`.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `4253aa225f47`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
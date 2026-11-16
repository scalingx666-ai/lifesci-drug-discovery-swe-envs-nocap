# Issue

**Title:** Mordred Service Pack 2

## Description

## Changes

Continues SP1: the remaining numerical divergences from mordred-community, plus two
ways `_new_mordred` could fail outright instead of returning a wrong number. Found by
comparing against mordred on MolPILE and MoleculeNet molecules.

**Numerical agreement**
- **Autocorrelation:** built from the mean-centered property, so that what cancels
  exactly for a property equal on every atom comes out as an exact zero instead of
  residue the guards downstream don't recognise. Fixes MATS/GATS.
- **BCUT:** 24 columns were emitted in our property order. The layout is set by name in
  `utils/feature_names.py`, not by a descriptor's internal list, so the fix belongs
  there.
- **ETA:** intermediate `float32` casts cost precision at comparison thresholds; only
  the final cast to the output dtype remains.
- **Tests:** the end-to-end comparison skipped any feature that was NaN on both sides
  for every test molecule, which is how unimplemented descriptors stayed out of it.
  Nothing is left for it to hide, so the mask is gone and every feature is compared.

**Timeouts**
- `DetourMatrix` and `MolecularId` enumerate simple paths, which is exponential in the
  number of independent cycles, so either can run for hours on a fused molecule. Both
  now take a deadline, as the `timeout` constructor parameter, defaulting to the 60 s
  mordred gives its detour matrix. Unlike mordred, `MolecularId` is covered too —
  upstream leaves it unbounded and it has been measured at 16 s on one molecule.
- `max_ring_system_rank` (default 23) drops a ring system with more independent cycles
  than that without searching it: the search costs ~2.2x more per cycle, so past that
  it only burns the timeout without producing a value.
- An abandoned search gives NaN, as mordred's error objects convert to, and warns with
  the molecule and the reason — otherwise it is indistinguishable from the other
  reasons a descriptor comes out NaN.

**CalcSASA crash**
- `use_3D=True` killed the process on 1425 molecules of a 25k MolPILE sample (`[Zn]`,
  `[Na+]`, `[Ar]`, `[C]`). A SIGSEGV, so no `try`/`except` caught it, and under joblib
  it took down the whole job.
- Upstream bug in the freesasa RDKit vendors: `sr_atom_area` reads an atom's first
  neighbour before checking it has one ([`sasa_sr.c:312`](https://github.com/mittinatten/freesasa/blob/9432950/src/sasa_sr.c#L312)),
  and the array is `malloc`ed uninitialised ([`nb.c:286`](https://github.com/mittinatten/freesasa/blob/9432950/src/nb.c#L286)).
  Present in 2.0.3 (the pinned version), 2.1.3 and `master`; unreported.
- The trigger is per atom: atom *i* is unsafe when no other lies within
  `(r_i + probe) + (r_j + probe)`. A lone counterion in a large molecule hits it too, so
  a guard on atom count would leave the crash in. Such atoms are withheld from
  `CalcSASA` and get their exact `4*pi*(r + probe)^2`; nothing occludes them and they
  occlude nothing, so the rest is unchanged.
- Also fixes silently wrong values: where the garbage index landed on mapped memory, a
  lone argon returned 31.09 instead of 135.19, with no warning.

## Validation

- **2D:** over 3000 MolPILE molecules, 58 of 1613 features change value. All 58 agree
  with mordred more often than before, none less; 172 860 → 173 999 agreeing values.
  `ETA_eta_B` goes from 2664/3000 to 3000/3000.
- **3D:** 213 3D-only features against mordred-community 2.0.7 over MolPILE 25k, shared
  conformers, `rtol=1e-4`: **172/213 features with no difference at all**, the other 41
  all SASA (known FreeSASA deviation). 24 711 molecules compared, of which 2757
  single-atom ones that used to crash the run.
- **Crash:** 0 crashes in 25 fresh processes on `[Zn]`/`[Ar]`, against roughly half
  before; all 18 260 feature values over 10 drug-like molecules bit-identical to before
  the change, so the common path is untouched.
- mordred returns NaN where we return a value on 1773 values / 35 features, never the
  other way round. Those are elements past Z=103, where mordred's vdW table ends and
  RDKit answers with its 2.0 placeholder — so this is against us, not for us. Fixing it
  means pointing `utils/sasa.py` at the mordred radii table the rest of the code uses;
  left out here because it moves the SASA reference values.

**Tests**
- Three regression tests for the crash: a single atom, two atoms out of reach of one
  another, and a contacting pair plus a distant lone atom.
- Suite green over 3652 tests.

## Checklist before requesting a review
- [x] Docstrings added/updated in public functions and classes
- [x] Tests added, reasonable test coverage (at least ~90%, `make test-coverage`)
- [x] Sphinx docs added/updated and render properly (`make docs` and see `docs/_build/index.html`)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `05b805b0ad67`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
# Issue

**Title:** fix(hetero): interface orientation normalization, bulk rebuild crash, bulk grid scan + OTP input width

## Description

## Problems

1. **Exported/built slab heterostructures could render upside-down**: the interface cell inherits the substrate slab's c direction, so a c-down substrate produced a c-down interface (cell drawn downward against the world axes, grid-scan extxyz exports flipped).
2. **~Half of all ZSL slab matches produced left-handed cells** (negative determinant): `_align_sl_vectors` swaps the matched a/b superlattice vectors to align a with the input substrate, flipping the in-plane determinant. VASP rejects a negative triple product.
3. **Bulk mode: clicking Generate Interface twice exploded the structure** — the built interface replaced the pane structure and was fed back in as the "bulk substrate" for the next build.
4. **Bulk mode had no Stacking Grid Scan** section (slab-only), and the intermat result did not guarantee substrate-first atom ordering, which the scan's film-atom slice relies on.
5. **HPC 2FA verification-code input collapsed to ~1 character wide** (unusable): the shared `.draggable-pane .apply-btn { width: 100% }` rule squeezed the `flex: 1` input in the OTP row.

## Fixes

- `_normalize_interface_orientation` (Python + faithful Rust/WASM port): c-down interfaces get a rigid 180° rotation about the a-axis (proper rotation — chirality, stacking order, and interatomic distances preserved); left-handed cells are relabelled `b -> -b` (same Bravais lattice, Cartesian positions unchanged). Applied at the end of slab stacking and on structures entering `/grid-scan`, so previously-built flipped interfaces are corrected on re-scan.
- All heterostructure build paths track built outputs and rebuild from the original substrate (slab / manual / bulk / lateral).
- Bulk mode gets the grid-scan section; intermat results are reordered substrate-first ("bottom" props) before returning.
- Grid scan runs on a snapshot of the built interface (no shift compounding after applying an entry); stale scan results are cleared on rebuild.
- Molecule principal-axes alignment keeps the input vertical sense (eigenvector sign ambiguity could display molecules upside-down).
- OTP row scopes the submit button back to auto width.
- Repaired the `heterostructure_compat` Rust test (missing `twist_angle` arg — it did not compile on main — plus coincident test atoms silently dropped by the build's dedup filter, and the hex gamma expectation for the now right-handed cell).

## Verification

- Python: end-to-end slab search -> build over 10 matches, all now right-handed with c up; a c-down substrate yields a c-up interface; internal distances unchanged; normalization is idempotent; grid-scan entries inherit the corrected cell.
- Rust: full `cargo test` suite passes (1056 tests incl. the repaired compat tests); WASM rebuilt.
- `vitest` suite passes; `svelte-check` reports no new errors in the touched files.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0649cc8149be`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
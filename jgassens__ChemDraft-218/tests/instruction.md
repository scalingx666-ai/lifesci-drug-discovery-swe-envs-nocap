# Issue

**Title:** Let RDKit's 3D cleanup account for separate molecules in one structure

## Description

## Summary
The vendored RDKit build gains patch `0008`: `optimize_3d_conformer` accepts an optional `ignoreInterfragInteractions` boolean and passes it to the MMFF and UFF minimizers.
- **Left out:** it defaults to `true` and behaves exactly as before.
- **Set to `false`:** a structure made of several separate molecules (a host and a guest, say) is minimized with the forces between them, so they no longer pass through each other.

No caller sets the option yet.

## Changes
- `vendor/patches/0008-…minilib.cpp.patch` (one file); the WASM is rebuilt from `Release_2026_03_3` with patches 0001–0008 via Colima/Docker.
  - The `.js` glue is byte-identical; the `.wasm` grew by 185 bytes.
- Pins updated: `PINNED_RDKIT_WASM_SHA256`, `vendor/BUILD.md` (new patch row, eight-patch budget), `dependency-inventory.md`, and `NOTICE`. NOTICE changed because its RDKit entry states how many local patches the build carries ("7 patches" → "8 patches"); a test checks that count. The licence is unchanged.
- `conformer.ts` forwards the option only when a caller sets it, so the request JSON is unchanged otherwise.

## Tests
- `optimizeDefault.real.test.ts`: exact-string golden test of the default path for 3 molecules × MMFF94/MMFF94s/UFF. It passes against **both** the previous and the rebuilt WASM, so the default output is byte-identical.
- `interfragOptimize.real.test.ts`: starts from a 1.87 Å overlapping start.
  - With the option on, the closest heavy-atom contact goes to 3.81 Å (UFF) and 4.12 Å (MMFF94s).
  - Left out, the fragments stay overlapping, which proves the flag is read by value.
- Gauntlet on macOS:
  - `pnpm lint` ✓, `pnpm vitest run` ✓ (9,434), `git diff --check` ✓
  - cargo fmt / clippy / test ✓ (568)
  - `pnpm build` compiled, then failed only at local DMG packaging (`bundle_dmg.sh`, unrelated).
- Spin 3D suites (`spin3dModel`, `spinFlatten*`, `flattenRoundTrip`, `spinOverlay`, `rotation3d`): 136 passed.

## Platforms
- **macOS:** verified (tests above).
- **Windows:** unverified. It needs a check that Spin 3D still works and that the new WASM loads.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ecb104e884a5`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
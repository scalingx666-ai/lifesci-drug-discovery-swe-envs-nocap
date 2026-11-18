# Issue

**Title:** Write the real resolution into TIFF exports

## Description

## Summary

TIFF exports declared a resolution of 1/1 with no unit, so Word, Preview and Photos read them as "1 dpi" and could place them at the wrong physical size. They now declare the same density as PNG exports: the scale actually applied, after any size clamping, times the 96 px/inch convention of the source SVG, with the unit set to inches. So a 1× export is 96 dpi and a 3× export is 288 dpi.

- TIFF is now encoded with the `tiff` crate directly. The `image` 0.25 wrapper cannot set resolution tags. The encoding otherwise matches what `image` wrote before: RGB8 flattened onto the background, uncompressed, same strips. Only the resolution tags differ.
- `tiff` 0.11.3 was already shipped through `image`; it is now a direct dependency at the same locked version (MIT). `Cargo.lock` gains one direct-dependency line, and `docs/architecture/dependency-inventory.md` gains a row. No new third-party code.
- PNG, JPEG, BMP and GIF output is unchanged.

## Known limitations

- A TIFF export at an applied scale below about 1/19200 now fails with a specific error instead of writing a file. Such a scale is not reachable from the export dialog.
- An invalid `cssPxPerInch` now fails a TIFF export, just as it already fails a PNG export.

## Tests

- New Rust tests in `export.rs`: 96 dpi at 1×, 288 dpi at 3×, density after max-dimension clamping, fractional densities kept as reduced rationals, and 96 dpi when no density is given. Each reads the tags back and compares every pixel.
- Gauntlet on macOS at e0c81b06: `cargo fmt --check`, `cargo clippy --all-targets -D warnings`, `cargo test` (654 passed), `pnpm lint`, `pnpm build`.
  - `pnpm vitest run`: 13317 passed. The one failure is in `tools/agent-skill/stress/runner/runner.test.ts`, which this branch does not touch; that file fails only under full-suite load and passes 57/57 on its own.

## Platforms

Shared Rust with no platform branches.
- Windows: hands-on PASS at e0c81b06. Windows' own TIFF reader reports 96 dpi in inches (both axes) at 1× and 288 dpi at 3×, and the pixels are identical to the PNG exports.
- macOS: no hands-on run planned. The change is platform-free Rust, and its tests read the resolution tags back. The agent that runs Mac hands-on tests cannot get past the save dialog, so the Windows check plus these tests cover it.

## Review

- Claude Opus 5.5, run-20261101-155359-68065c: approved; 5 low or nit notes, two of which are listed above.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3ee241074ade`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
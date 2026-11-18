# Issue

**Title:** Preserve export chemistry and harden session and filename safety

## Description

## Problem

Fallback SMILES could silently export a neutral radical as a closed-shell molecule, and a stored
SMILES string could hide a later radical mark. The engine-backed SMILES/SDF paths could also turn
supported condensed labels such as `NH2` into dummy atoms because they omitted the existing label
speller. Separately, an empty dirty document could bypass the Windows updater's strict save guard,
and batch names accepted Windows device names that document output already refused.

## Solution

- Bracket radical-bearing atoms, spell their hydrogen counts, and regenerate fallback SMILES from
  the current graph when radical marks exist.
- Pass the shared single-heavy-element label speller to the SMILES and SDF molfile writers.
- Permit an unavailable strict save to be skipped only for clean blank canvases or clean saved files.
- Share Windows device-name detection between batch names and document output.
- Fix the existing art-engine license test's transitive-dependency lookup under pnpm.

## Files changed

- `packages/document-workflow-core/src/{smiles,moleculeSmiles}.ts`: chemical export preservation.
- `apps/desktop/src/{structureListExport,documentSession}.ts`: SDF labels and strict save guard.
- `packages/chemdraft-cli/src/{output,documentInput}.ts`: portable output-name validation.
- `tools/bug-audit.test.ts` and the affected existing export/session tests: regression coverage.
- `packages/art-engine/src/index.test.ts`: owner-scoped dependency lookup; no dependency change.
- CLI documentation, scoped plan, proposed bug-fix notes, and the required desktop build stamp.

No personal launch scripts, generated files, new dependencies, or schema changes are included.

## Validation

The 27 new regression cases were run against the unchanged base commit:
22 failed and 5 passed. After applying the fixes, all 27 passed. Real RDKit WASM checks cover the
radical and supported condensed-label examples.

Completed in a clean macOS checkout using the locked dependencies and Node 24.19.0:

- `node node_modules/typescript/bin/tsc -p tsconfig.json --noEmit`: passed.
- `node node_modules/vitest/vitest.mjs run tools/bug-audit.test.ts --maxWorkers=1`: 27 passed.
- Seven targeted existing suites: 186 passed.
- `node node_modules/vitest/vitest.mjs run --maxWorkers=2`: 342 test files passed, 6 skipped;
  **6,961 tests passed, 25 skipped, zero failures**. This complete run uses the corrected assertions.
- From `apps/desktop`, `node node_modules/vite/bin/vite.js build`: passed.
- `git diff --cached --check` and patch application against the base commit: passed.

The complete suite ran outside the filesystem sandbox so CLI subprocesses could open their local
IPC sockets. No tests were excluded to obtain the passing full-suite result. Tests marked skipped
by the existing project remain skipped. Browser-build warnings about large chunks and a dependency
annotation remain; the build completed successfully.

## Limitations

Native macOS and Windows builds and the both-platform manual checklist have not been run here:
Rust/Cargo is unavailable. The updater test simulates a refused save; it does not install a real
Windows update. Filename validation is tested, but native Windows device-file operations were not
executed. Cross-platform CI and native verification are required before merge/release.

Prepared with AI assistance (OpenAI Codex); the implementation and regression evidence are provided
for maintainer review.

## Maintainer review and verification

- **Caught up with main** (only the build stamp conflicted). `PLANS.md` keeps main's text; the notes stay in `docs/bug-fixes/export-session-safety.md`.
- **Review fix** (`a40db4b4`): a condensed label carrying radical electrons, such as `CH3` with two radical marks, was spelled as `[CH3]` (one radical) with no warning. Such labels now keep the `*` placeholder and the loss warning on the SMILES and SDF routes. `isWindowsDeviceName` also covers `COM¹`–`COM³`, `LPT¹`–`LPT³`, `CONIN$` and `CONOUT$`.
- **Out of scope:** some radical cases already fail on main (literal `C`, metals, D, counts above two through the V2000 writer, pasted `M  RAD` lines). They will be fixed separately.
- **CI:** all four hosts pass.
- **macOS, by hand** (packaged build of `a40db4b4`): Copy As SMILES gives `[CH3]` for a methyl radical, `CN` for C–NH2, and `[*]` plus a named warning for CH3 with two radicals.
- **Windows, by hand** (release build of `a40db4b4`, CDP drawing input, native Save dialog): the same three cases pass through Copy As SMILES, `.smi` and SDF. CLI batch names `CON`, `COM1`, `nul`, `aux` and `LPT1` are refused with exit 2.
- **Not run natively:**
  - The updater strict-save guard, on either platform, because there was no newer update feed to install. Unit tests and a review trace of every caller of `strictSessionFlushRefusal` cover it.
  - SDF export on macOS. The Windows run and a real-RDKit test cover it.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `101072d4edca`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
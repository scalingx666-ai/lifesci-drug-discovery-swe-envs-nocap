# Issue

**Title:** Send keys to the hovered atom or bond after a hover relabel

## Description

## Summary

With the ChemDraft key scheme, keys act on whatever the mouse is over. After labelling an atom by hovering and typing, the next key was taken as more label text for that atom even after the mouse had moved on:

- ethane: `o` on one carbon, move to the other, `o` gave the literal label "Oo" on the first carbon instead of HO–OH;
- `o`, then `5` over the new C–O bond gave "O5" instead of fusing a five-membered ring (THF); the same for `2`, `4`, `6`, `7` and `8`.

Now, once the mouse has left the labelled atom and its own bonds:

| Mouse is over | Key | Result |
|---|---|---|
| a different atom | element key (either case) or digit | acts on that atom |
| a bond (including the labelled atom's own) | bond or ring digit | acts on the bond |
| empty canvas or another bond | lowercase letter that completes a real element (S+i, C+l, B+r) | continues the label |

Deliberate typing while the mouse drifts (OMe, CF3, NO2) is unchanged. Element symbols come from chem-core's `elementSymbols`, not a new list.

**Changed test expectation:** one older test expected `o`, move to another atom, `2` to type "O2" on the first atom. The digit now runs that atom's own hotkey (it adds a carbonyl), which is what the bug report asks for.

## Tests

- `hoverLabelTyping.dom.test.ts`: 92 tests on both shortcut platforms, including HO–OH (lowercase and uppercase), ring and bond digits over the bond, N/move/o (no nobelium on the old atom), Si/Co/Sn completion, and digit keys over another atom, each compared with a run that has no label in progress. A focus test uses DOM keyboard and pointer events, not the agent bridge.
- Full suite: `pnpm lint`, `pnpm vitest run`, `pnpm build`, `git diff --check`, `cargo fmt --check`, `cargo clippy -D warnings`, `cargo test`, all passing on the merge with current main.

## Platforms

Hands-on is **not yet verified** on either platform. Hover typing in the macOS and Windows webviews still needs the runbook pass.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a99ec5122cf4`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
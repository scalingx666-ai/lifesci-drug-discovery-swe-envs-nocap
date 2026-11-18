# Issue

**Title:** Keep the atom when a label with the same head element is typed on it

## Description

Typing a label on an atom that already has bonds used to attach a *new* atom when the label started with the same element. Editing a two-bond P shown as PH to PPh2 added a second phosphorus, and typing SH on the S of CH3–S(=O) added another sulfur.

## What changes
- A typed label whose head is the same element as the bonded atom now **relabels that atom in place**, keeping its id, bonds and charge. If the result is over-valent, the usual invalid-valence warning shows.
- Abbreviation-table labels (OMe, OEt, NO2 …) still attach as substituents.
- An atom carrying an isotope refuses a group label that cannot keep the isotope, with a specific message that says how to get past it ("…clear the isotope first to relabel"), on the hover-typing path too, instead of silently dropping the isotope. Typed Ac, Pr and Ts are covered.
- With hover typing, moving to another atom and pressing a key commits the open label first. If that commit is refused, the key is no longer passed on to the new atom: the refusal message stays on screen and nothing else changes. If the commit succeeds with a warning, the key still acts and both messages show, warning first.
- The valence warning for a typed label such as SH now says what it means, e.g. "SH puts 5 bonds on S (4 from bonds to other atoms + 1 H); neutral S normally makes 2." instead of "SH accounts for 5 of 2 bonds."; the badge itself is unchanged. (Relabelling in place makes this warning appear more often.)
- A refused fallback no longer reports "Relabeled" or deletes the Text tool's text box, and a commit that changes nothing shows no status.

## Behaviour that changes for existing drawings
These used to add a second atom and now relabel in place, with a valence warning where one applies:
- NHMe / NMe2 typed on a two-bond N
- OBn / OTBS typed on an O+
- SMe / SPh typed on the S of an S(=O)
- SiMe3 typed on Si

The N cases have their own tests; the O, S and Si cases follow from the same head-element rule and are checked in the hands-on runbook.

## Tests
New cases in document-workflow-core, the app's label tests and hoverLabelTyping.dom.test.ts cover in-place relabel, isotope refusal (also across a hover hand-off), no-op commits and the Text-tool box. One existing expectation changed: the CH3 case of `documentWorkflow.isotopes.test.ts` (from #245), typed and untyped, used to expect carbon-13 relabelled to CH3 with the isotope dropped. It now expects the refusal (document unchanged, atom stays carbon-13, refusal text reported), because silently dropping an isotope breaks AGENTS.md §7 and matches this PR's other isotope refusals. Keeping the 13 as ¹³CH₃ is logged as a follow-up. Every quote of the refusal message now includes its new hint, "clear the isotope first to relabel".

## Platforms
- **macOS:** hands-on runbook steps 1–7 passed at 2dd75046 (stamp 11.01.14.03-codex). After step 7's unchanged commit the status line keeps "Editing atom label"; that comes from a path this PR doesn't touch and is logged as a follow-up.
- **Windows:** steps 1–7 passed at 3c0e2e4d; steps 1, 2, 5 and 6 re-checked at 2dd75046 (stamp 11.01.14.03-codex), with the exact new valence and isotope messages.
- CI: macOS, Linux and Windows jobs.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0d73dffbf68e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
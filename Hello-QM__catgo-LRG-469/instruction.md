# Issue

**Title:** fix(terminal): synthetic post-commit DELs no longer erase committed CJK

## Description

## Symptom

Typing Chinese in the terminal intermittently swallows characters at the candidate-commit stage (时吞时不吞, no clear trigger).

## Root cause — two IME fixes fighting

1. After a composition commits, the guard **clears the textarea** so xterm's deferred `_finalizeComposition` can't re-send the composed text. The clear makes xterm's `_handleAnyTextareaChanges` see a length decrease and emit **synthetic DEL(s)**.
2. A comment claims those DELs are swallowed by the residue window — but the later "never swallow Backspace" fix (added because a stuck `std_composing` once ate real backspaces) forwards `\x7f` **unconditionally**.

Result: every commit can be followed by synthetic backspaces that erase the tail of the just-committed Chinese. Whether they fire depends on xterm's internal `setTimeout(0)` timing — hence intermittent.

## Fix

**DEL debt**: at clear time, arm a debt equal to the cleared length. Within the post-compose residue window, `\x7f` chunks are consumed against the debt (synthetic); anything beyond the debt, after the window, or after any non-DEL input passes through as a real backspace. Applied to both the desktop `TerminalPanel` inline guard and the mobile `terminal-ime` guard (new `note_textarea_clear`).

## Tests

+4 guard tests (exact-count eating, batched chunk, window expiry, cancellation by other input); the existing never-swallow-real-Backspace regression still passes. Full suite: 4,414.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d2b3c01ec3ae`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
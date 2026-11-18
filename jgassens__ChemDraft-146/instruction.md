# Issue

**Title:** Floating toolbars hide while an in-app dialog is open

## Description

ChemDraft's own in-app dialogs (Export, the close-tab prompt fallback, Add or Remove Plugins, Customize Toolbars, plugin text/image prompts, recognition install, the enlarged linked figure) left the native floating toolbars and plugin panels on top of them, so a toolbar could cover the dialog's fields (seen with File ▸ Export on both platforms). Native message boxes and file dialogs already hide them through the shared utility suspension (#131, order-preserving restore #140).

Now `useInAppModalUtilitySuspension` (one `MutationObserver` in the document window on `OPEN_MODAL_DIALOG_SELECTOR`, the same definition the shortcut blocking uses) holds exactly one shared suspension while any in-app modal is open:
- toolbars hide when the first modal opens and come back, in the same order, when the last one closes;
- a native picker opened from inside a modal (Export ▸ Choose…) shares the counter, so toolbars stay hidden until both are gone;
- the suspension is released on close, unmount or observer error, and quit refusals are handled without blocking;
- CSS-hidden dialogs don't count, and the web build is unaffected;
- observer scans are limited to inserted subtrees.

This is the interim fix. Under the owner's new rule (#145) these dialogs move into their own native windows over time, and the same shared suspension carries over to them.

**Tests:** acquire/release once per open/close; two modals in either order; a native dialog inside a modal; unmount while open; CSS-hidden modal ignored; no calls in the web build; both simulated platforms. `pnpm lint` ✓; 448 tests in the affected suites ✓ (macOS).
**Platforms:** macOS hands-on below; Windows run to follow.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `14b9ae657a76`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
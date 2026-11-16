# Issue

**Title:** #12554 - Restore language selector in Settings

## Description

## Summary

Restores the language selector in the General section of the Settings dialog. It was removed as a side effect of the Settings redesign in #12354, which left multi-language builds (`KETCHER_MULTI_LANGUAGE_BUILD=true`) with no way to switch the interface language from the UI.

```
Settings → General Editing & Display
  Language        [ English ▾ ]   ← restored here, when SUPPORTED_LANGUAGES.length > 1
  Reset to Select Tool
  ...
```

The selector keeps the previous behavior: it renders only when more than one language is available, uses the existing `settings:language.title` key, keeps `data-testid="language-select"`, and calls `i18n.changeLanguage()` immediately, independent of the dialog's Apply/Cancel flow.

## Evidence

**Before:** the General section had no Language field (removed in #12354 / `4ca29886b9`).

**After:** the Language field appears at the top of the section and switches the UI live.

![Language selector in Settings](https://raw.githubusercontent.com/spalax-dev/ketcher/b038eb2c688473cb0d56fb8880fd0db2cf71d3a5/evidence/12554/ui-settings-language.png)
![Settings in Simplified Chinese](https://raw.githubusercontent.com/spalax-dev/ketcher/b038eb2c688473cb0d56fb8880fd0db2cf71d3a5/evidence/12554/ui-settings-zh.png)

- Regression test: `packages/ketcher-react/src/script/ui/views/modal/components/meta/Settings/__tests__/Settings.test.tsx`
  - The first test fails on `master` (no `language-select` in the rendered dialog) and passes with this change.
  - The second test selects `简体中文` and asserts `i18n.changeLanguage('zh-CN')`.
  - `npx jest .../Settings.test.tsx` → 2 passed.
- `npx prettier --check` and `npx eslint --quiet` on both files → clean.
- `KETCHER_MULTI_LANGUAGE_BUILD=true npm run build:packages` → success.

### Verified in the app

Molecules mode, standalone (Vite dev server), built with `KETCHER_MULTI_LANGUAGE_BUILD=true`:

- Opened Settings from the toolbar; the Language select rendered with `English`.
- Selected `简体中文`; the panel re-rendered immediately (title `设置`, selector `简体中文`, section `常规编辑与显示`), with no page reload.
- Console errors: none.

Not verified: macromolecules mode visuals, remote mode.

## Merge Danger

**Door:** two-way

Restores behavior that README, the localization spec and `.memory-bank/modules/i18n.md` already describe. No public API change, no change to file formats or saved settings. English-only builds are unaffected: the control is gated on `SUPPORTED_LANGUAGES.length > 1`.

**Blast Radius:** settings-dialog

The Settings panel is shared by both editor modes; only multi-language builds render the restored control.

---

Memory bank: not needed

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `48af1b20d586`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
# Issue

**Title:** #12556 - Spanish (es) interface localization

## Description

## Summary

Adds a complete Spanish (`es`) locale to both UI packages: the six `ketcher-react` namespaces (`common`, `toolbar`, `toolbars`, `dialogs`, `components`, `settings`) and the two `ketcher-macromolecules` namespaces (`macromolecules`, `macromoleculesDialogs`). 806 keys, mirroring the `en` structure exactly.

This is **data-only**: no i18n code, build-flag or public API changes. The locale is discovered by the existing resource generator and appears automatically in a `KETCHER_MULTI_LANGUAGE_BUILD=true` build.

```
packages/ketcher-react/src/locales/es/*.json            6 files
packages/ketcher-macromolecules/src/locales/es/*.json  2 files
packages/*/src/i18n/localeResources.generated.ts       + es registration
README.md                                              supported languages
```

## Evidence

- Key parity against `en`: 0 missing, 0 extra across all eight namespaces.
- ICU placeholders: 0 mismatches (`{count}`, `{shortcut}`, `{name}`, `{value}`, …).
- `tsc --noEmit` passes in `ketcher-react` and `ketcher-macromolecules` (the generated `satisfies` check validates `es` against `en`).
- Rendered check with `KETCHER_MULTI_LANGUAGE_BUILD=true`: Settings, toolbars and dialogs render in Spanish with no raw keys.

Spanish UI with the locale active (`localStorage["ketcher-language"]="es"`):

![Spanish toolbar](https://raw.githubusercontent.com/spalax-dev/ketcher/c5e4e20f799d233c3676f8e9de8f382e31ea2c8a/evidence/12556/es-app-toolbar.png)
![Spanish Settings](https://raw.githubusercontent.com/spalax-dev/ketcher/c5e4e20f799d233c3676f8e9de8f382e31ea2c8a/evidence/12556/es-app-settings.png)

Current `master` includes the restored language selector (#12555). With master merged into this branch, Spanish appears in **Settings → General → Language** as `español` and switches the UI live:

![Spanish selected in Settings](https://raw.githubusercontent.com/spalax-dev/ketcher/d90de85d88996450a097d2e333cd888a6f41211c/evidence/12556/selector-es.png)

Note: the dev server emits a few pre-existing i18n `missingKeyHandler` warnings while Settings is open (enum values passed through `t()`, and `hint` strings translated twice). They appear identically with English and only in development builds, so they are unrelated to this locale.

## Merge Danger

**Door:** two-way

Adds translation data only. The English-only default build is unchanged (the locale is tree-shaken out without the flag), there are no API or file-format changes, and chemistry vocabulary remains untranslated.

**Blast Radius:** multi-language-builds

Only builds with `KETCHER_MULTI_LANGUAGE_BUILD=true` gain a new locale; English behaviour is unchanged.

---

Memory bank: not needed

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2202909801d5`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
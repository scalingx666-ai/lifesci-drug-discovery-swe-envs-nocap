# Issue

**Title:** Neutral Spanish across regions, with a Spain override for Settings

## Description

. These three commits were pushed after #7 merged, so they aren't in `main`.

## What changes

**Neutral Spanish, 274 strings.** Six regional reviewers each read the whole table: Mexico, Central America and the Caribbean, Colombia and Venezuela, the Andes, the Southern Cone, and Spain. A string kept its wording only if no region found it odd; the rest took the least regional option from a glossary backed by the RAE, Fundéu, and Apple's and Microsoft's Spanish terminology. The owner, a native Colombian speaker, reviewed the result on device.

- **Words that marked the text as from Spain:** añadir → agregar, introducir → escribir, pauta → esquema, prospecto → ficha técnica, comprimido → pastilla (Cápsula stays separate), pomelo → toronja (pomelo).
- **Rephrased where no single word works everywhere:** "se reporta" sounds foreign in Spain, and valorar and calificar each mean something else in some regions.
- **Double meanings removed:**
  - curado means "drunk" in Chile
  - tirar is slang in Colombia and the Andes
  - "sustancia base" reads as cocaine paste in Colombia
  - revisión (check-in) → seguimiento
  - despejado means wide awake in Spain
- **Owner's choices:**
  - Insights → **Tendencias**; "análisis" is the app's own word for a blood test.
  - Afterglow → **Residual**.
  - Evening → **Anochecer**.
  - Threshold → **Sutil**.

**Spain override for Settings.** iOS names the Settings app "Configuración" in Latin America and "Ajustes" in Spain, so no one word matches every phone. `es` says Configuración, and a new `es-ES` localization overrides only the 14 strings that name Settings (`ES_ES` in `localization/es_translations.py`). **iOS has no per-key fallback from es-ES to es.** A partial table showed English on a Spain iPhone, which I caught on the simulator. `translate_catalog.py` therefore writes the whole es-ES column as `{**ES, **ES_ES}`.

**Claims stay hedged.** Dropping "reportar" had turned "commonly reported" into "es frecuente" ("it is frequent"), which states a frequency as fact. Those strings now read "se describe con frecuencia", and "Most reported" reads "Más mencionados".

**Casual notifications.** For example:
- "Ventana de pico estimada según datos de referencia" → "Por lo general, más o menos ahora llega al pico. ¿Cómo te sientes?"
- The hydration reminder → "Recuerda beber agua cuando puedas".

**Pharmacological target.** In labels it's "Dónde actúa", and in explanations "sitio de acción". "Objetivo" read as a goal and "diana" as a dartboard. "Objetivo" stays where the English means a goal (target dose, "Piru sets no target").

**Curated → "recopilado a mano".** "Revisado" claimed a check the data never had.

## Accuracy concerns for review

1. **Clearance → "eliminación".** Clearance is a specific rate, narrower than elimination. The current sentences read fine, but a label showing a clearance *value* would need aclaramiento (Spain) or depuración (Latin America).
2. **Package insert → "ficha técnica".** In Spain, ficha técnica is the prescriber document and prospecto the patient leaflet. It fits the FDA/DailyMed labels the app links to, but the two aren't strictly equivalent.
3. **Taiwan drug names.** The 18 zh-Hant corrections from #7 came from one reviewer's knowledge and weren't checked against Taiwan's official drug-license database. The benzodiazepines and opioids are worth a spot check.
4. **Tablet → "pastilla".** It's the everyday word, and some people use it loosely for capsules too. The app keeps Cápsula separate.
5. **"Qualified professional" → "un profesional de la salud".** Dropping "qualified" slightly softens the wording but doesn't change the claim.
6. **Ratings are phrased as "respuestas" (answers).** Valorar and calificar each read wrong in some region. The meaning holds.
7. **Literal numbers.** 0.001 g → "precisión de 1 mg" and 0.02 g → "≈ 17 mg" (3 mg ÷ 18 % = 16.7 mg), which avoids the comma-versus-point split. Both checked.
8. **Maintenance.** Any new string that names the Settings app needs an `ES_ES` line. Without one, Spain gets "Configuración", which is understandable but doesn't match the phone.

## Known gaps, not addressed here

- **Substance content is still in English for Spanish users,** because `ContentLanguage` resolves Spanish as English, as noted in #7. That covers descriptions and effects.
- **Some shared string keys need splitting in code:**
  - "Strength" covers both a drink's alcohol content and a pill's strength.
  - "Common", "Yours" and the mood row's "Low"/"High" have the same problem.
- **Time phrases.** "a las %@" should read "a la" at 1 o'clock; the fix belongs in code.
- **Widget and Live Activity** still show English substance names.
- **`%lld interaction%@ detected`** is a stale English-plural key and can't be translated. Remove it or replace it with the inflect version.

## Testing

- **Tests:** 2,178 Swift tests pass (`pipeline/run-tests.sh`), and SwiftFormat, SwiftLint and Ruff are clean. `translate_catalog.py` is a no-op on this branch. Every catalog has full es and es-ES coverage.
- **Simulator:** checked in es-ES (Ajustes, everything else Spanish) and es-CO (Configuración, Tendencias fits the tab bar).
- **Device:** on the owner's iPhone.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `84a5a4404054`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
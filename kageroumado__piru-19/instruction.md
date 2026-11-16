# Issue

**Title:** Effect Estimates: match transit absorption to PK Tmax

## Description

The effect engine's absorption now peaks at each drug's own Tmax (was a median ~1.9 h late), keeping the gradual oral onset.

Feeling peak time (hours):

| Drug | Dose | Published peak | Before | After |
| --- | ---: | ---: | ---: | ---: |
| Amphetamine | 50 mg | — | 2.83 | 1.58 |
| Methylphenidate | 60 mg | [~1.5](https://d-nb.info/1135151520/34) | 2.72 | 1.23 |
| 3-MMC | 50 mg | [1.00](https://www.nature.com/articles/s41386-024-02042-7) | 2.67 | 1.27 |
| Paroxetine | 50 mg | — | 3.33 | 1.77 |
| Tramadol | 200 mg | — | 1.75 | 0.93 |
| MDMA | 90 mg | [1.0](https://www.frontiersin.org/articles/10.3389/fphar.2023.1122861/pdf) | 2.23 | 1.15 |
| Sertraline | 50 mg | — | 3.32 | 1.78 |

Only the 3-MMC value is a dose-matched VAS “high” peak; methylphenidate uses VAS “good drug effect,” and the MDMA study used 100 mg.

Across all 38 effect-modelable substances, 35/36 scored now peak within 5 min of their Tmax.

<details><summary>Changed golden values (old → new)</summary>

| Test | Value | Old | New |
| --- | --- | ---: | ---: |
| Amphetamine | peak Feeling | 0.42 | 0.55 |
| Amphetamine | peak cardiovascular danger | 1.43 | 1.71 |
| 3-MMC | peak Feeling | 1.65 | 1.90 |
| Methylphenidate | peak Feeling | 0.09 | 0.20 |
| MDMA | peak Feeling | 1.19 | 1.77 |

</details>

Heroin's curated ka override remains unchanged; route kR and nAbs behavior remains in place.

Testing: EffectEngine and calibration-solver tests pass locally. CI build/test is blocked by the DoseRange Equatable/Hashable error, which also fails on main.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c59cb49a847b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
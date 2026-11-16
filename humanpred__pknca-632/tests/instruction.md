# Issue

**Title:** fix: make every AUCint dose-aware and exclude only when the half-life is used

## Description

, , .

## The problem (#508)

`aucint.*` reached across the doses on either side of the interval to find the concentration at the interval boundary. When a run of below-the-limit-of-quantification (BLQ) measurements sat before the next dose, `clean.conc.blq()` classified them as *middle* BLQ values — because the group's Tlast was in a later profile — and dropped them, so the interpolation ran *up* from Clast, through the BLQ region and over the next dose, to a measurement belonging to the next profile.

Minimal reproduction of the reported case — dosed at 0 and 24.1 hr, measurable through 7.59 hr, BLQ at 12/16/24 hr, measurable again at 24.654 hr, integrating 0–24 hr:

| parameter | before | after |
|---|---:|---:|
| `auclast` | 13.0 | 13.0 |
| `aucall` | 14.8 | 14.8 |
| `aucint.last` | **29.3** | **13.0** |
| `aucint.all` | **29.3** | **14.8** |
| `aucint.inf.obs` | **29.3** | **16.9** |
| `aucint.last.dose` | 19.6 | *(retired)* |
| `aucint.all.dose` | 19.6 | *(retired)* |
| `aucint.inf.obs.dose` | 16.9 | *(retired)* |

## What changed

**The doses bound the profile.** The profile being integrated ends at the first dose at or after `end`; a concentration measured after that dose belongs to a later profile and is neither integrated nor used to interpolate into this interval. The dose that *starts* the interval is not a bound in the same way — the trough at the start of a later dosing interval is still estimated from the profile before it, which `interp.extrap.conc.dose()` does without interpolating across the dose.

**Each dose within the interval starts a new profile.** The interval asks for the profiles on both sides of an interior dose to be integrated together, but the dose is a point to integrate to, the concentrations are cleaned one profile at a time, and the integration method is chosen one profile at a time. So the region after *each* profile's Tlast is handled by the AUC type within that profile, and an AUC over several dosing intervals is the sum of the AUCs over each of them.

**The region after Tlast is handled the way the matching AUC parameter handles it**, which is what the AUC vignette has always promised:

- `aucint.last` → contributes zero, so it equals `auclast` over a dosing interval
- `aucint.all` → the triangle from Clast to that profile's first BLQ measurement, so it equals `aucall`
- `aucint.inf.obs` / `aucint.inf.pred` → extrapolated with the half-life, always logarithmically; over a **finite** interval with no estimable half-life it falls back to AUCall (issue #508, item 3). Over an infinite interval it stays `NA`, since there is no bounded tail to fall back to.

Verified on q12h dosing with doses at 0/12/24/36, both with a pre-dose sample at every dose and with the 12 and 24 hr troughs missing, for intervals aligned with the doses and offset from them (6–30 hr):

| | 0–12 | 12–24 | 24–36 | 0–36 |
|---|---:|---:|---:|---:|
| `aucint.last` (troughs missing) | 37.05 | 43.65 | 75.22 | **155.92** = the sum |

**Dose awareness is the only method (#539).** Every `aucint`/`aumcint` parameter now takes the dose times, with a fallback to the previous whole-profile interpolation when no dosing data are given. The eight `.dose` parameters are retired; an interval specification asking for one gets an error naming its replacement, the same way `f` points at `f.obs`:

```
The following columns in 'intervals' are not allowed: aucint.last.dose
  'aucint.last.dose' is now named 'aucint.last'.
```

The method (`PPANMETH`) column reports both halves of #539's second ask:

```
AUC: lin up/log down. Interpolation: dose-aware. Extrapolation: half-life
AUC: lin up/log down. Interpolation: not dose-aware (no dosing data). Extrapolation: none
AUC: lin up/log down. Interpolation: dose-aware. Extrapolation: AUCall (half-life not estimable)
```

**A half-life exclusion only reaches an AUCint that used the half-life (#270).** An interval ending at or before Tlast is interpolated throughout, so `lambda.z` never enters the result. Those results are no longer excluded with the half-life, and they are calculated at all when the half-life is not estimable (which also revises #450). `exclude_nca_span.ratio()`, `exclude_nca_min.hl.r.squared()`, and `exclude_nca_min.hl.adj.r.squared()` read the extrapolation from the method column to decide, and keep the exclusion for any result that does not report one.

For a profile with `Tlast = 24` and the half-life excluded for a low span ratio:

| interval | parameter | exclude |
|---|---|---|
| 0–12 | `aucint.inf.obs` | *(none — interpolation only)* |
| 0–36 | `aucint.inf.obs` | `span.ratio < 5` |

## Bugs found in the dose-aware code

All were reachable before but are load-bearing now that dose awareness is the default:

- The route and duration of dosing never reached `interp.extrap.conc.dose()`, because the `pk.calc.aucint.*` wrappers had no `route` or `duration.dose` formals for `formalsmap` to fill. Every dose was treated as extravascular, so an intravenous bolus got no C0 back-extrapolation.
- `iecd_extrap_value()` passed a single concentration to `extrapolate.conc()`, so its AUCall branch could never find the first BLQ measurement after Tlast and always returned zero. It now passes the run of measurements back to the dose that started them.
- `iecd_extrap_value()` also used the caller's `clast` when extrapolating the trough *before* a dose, so the trough at the start of a dosing interval was computed from the Clast of the interval being calculated rather than from the Clast of the profile it decays from. The caller's `clast` (which is `clast.pred` for AUCinf,pred) now applies only when the run of measurements ends at the overall Tlast.
- `iecd_interp_value()` called `interpolate.conc()`, which aborts past Tlast. With a profile's trailing BLQ values now retained, both surrounding concentrations can be past Tlast, which is extrapolation; it uses `interp.extrap.conc()` instead.

## Notes

- The `aucint` values above are a user-visible change to existing analyses with dosing data. Analyses without dosing data are unaffected.
- `AUCINTD`, `AUCINTAD`, `AUCINTID`, and `AUCINTPD` go away with the `.dose` parameters. `AUCINTD` in CDISC is "AUC from T1 to T2 Normalized by Dose", which is not what `aucint.last.dose` calculated.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2d5a7acb6402`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
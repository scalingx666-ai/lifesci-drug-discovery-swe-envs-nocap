# Issue

**Title:** docs: add a half-life point selection decision tree to the v06 vignette

## Description

.

Adds an SVG flowchart to `vignette("v06-half-life-calculation")` covering the three ways the terminal-phase points can be chosen: automatic curve stripping, `exclude_half.life`, and `include_half.life`. It is a static checked-in figure, following the precedent already set by `v06-half-life-calculation-tobit_figure_1.svg`, so no new dependency is required — `html_vignette` base64-embeds it and pkgdown serves it as-is.

The tree documents two behaviors the vignette did not previously state anywhere, both confirmed by running them rather than by reading the source:

* `exclude_half.life` drops the flagged points and then runs the **normal** curve stripping, so `min.hl.points`, `allow.tmax.in.half.life`, and `adj.r.squared.factor` still apply to what remains. Only `include_half.life` sets `manually.selected.points = TRUE` and disables those three.
* Naming a point in `include_half.life` does **not** force it into the fit. BLQ and zero concentrations, and points at or before the end of the last dose, are dropped either way. Including eight Theoph points spanning a four-hour infusion gives `lambda.z.n.points = 5` starting at 5.1 h; including six points where one is BLQ gives 5.

The existing `NA`/in-use prose moves into a table under a new "Column Requirements" heading, unchanged in substance.

### Verification

* Vignette renders: one `<img>`, SVG base64-embedded, alt text and table intact.
* `spelling::spell_check_files()` clean, no `inst/WORDLIST` additions needed.
* No files under `R/` changed; `_pkgdown.yml` needs no update since it does not enumerate vignettes.

### Note for the reviewer

The SVG is hand-authored, so it is a second place to edit if the include/exclude logic is ever revised. That matches the existing Tobit figure, but it is a deliberate trade-off rather than an oversight.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c217f0628d51`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
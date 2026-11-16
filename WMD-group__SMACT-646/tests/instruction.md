# Issue

**Title:** docs: describe the dopant workflow accurately and sharpen the pymatgen comparison

## Description

Addresses #642, raised by @crispppp during the JOSS review (openjournals/joss-reviews#11015).

## 2. Ionic-radius constraints in dopant prediction

The reviewer is right, and the discrepancy was in two places, not one. `smact/dopant_prediction/doper.py`'s module docstring said the search was based on "chemical filters (e.g. difference in ionic radius)", and the paper's Software Design section repeated it. There is no radius criterion anywhere in the module. What `Doper` actually does:

1. filters candidate species on oxidation state — an n-type dopant must carry a more positive charge than the host ion it replaces, a p-type dopant a more negative one, with sign guards for anion and cation sites;
2. ranks survivors by substitution probability from the data-mined lambda table [Hautier et al. 2011], or by cosine similarity in a species embedding (`skipspecies`, or either M3GNet ion embedding);
3. optionally adds a selectivity score — a dopant's probability for one host site divided by its summed probability across the others — and a combined score weighting similarity 0.75 to selectivity 0.25.

Both descriptions now say that. They also explain *why* there is no radius filter, which is the more useful answer: `Doper` works from a composition, and Shannon radii are defined per coordination number, which is not known without a structure. `smact.Species` bears this out — its signature is `Species(symbol, oxidation, coordination=4, radii_source="shannon")`, so a radius cannot be looked up until a coordination number is assumed. The docstring now points callers who *do* have a structure at `pymatgen.analysis.structure_prediction.dopant_predictor.get_dopants_from_shannon_radii`.

I did not add a radius-based workflow. That would be a feature, not a correction, and it would need a coordination-number input that the composition-first API does not currently have. Happy to open a separate issue for it if the reviewer would prefer that to a documentation fix.

## 1. Statement of need and added value relative to existing tools

The previous State of the Field argued SMACT's niche in general terms — "composition level, upstream of structure-based tools" — which does not answer a reader who knows pymatgen ships the same substitution model. It now names the overlap and draws the line concretely:

- pymatgen implements the same data-mined ionic substitution model in `SubstitutionProbability`, `SubstitutionPredictor`, `Substitutor` and `SubstitutionPredictorTransformation`, and predicts dopants via `get_dopants_from_substitution_probabilities` and `get_dopants_from_shannon_radii`.
- **Both** of pymatgen's dopant predictors require a crystal structure decorated with oxidation states; the radius-based one additionally requires a bonded structure graph (e.g. from `CrystalNN`). I verified this against pymatgen 2025.4.24: passing a species list to `get_dopants_from_substitution_probabilities` raises `AttributeError: 'tuple' object has no attribute 'species'`, whereas `Doper(("Ti4+", "O2-")).get_dopants()` returns Ta5+ and Nb5+ as the leading n-type substitutions for Ti4+ with no structure involved.
- SMACT's structure prediction pairs the substitution model with a local, species-indexed structure database (`StructureDB.get_with_species`), so candidate compositions are matched against parent structures in bulk rather than one transformation at a time.

And the "build vs contribute" question the JOSS checklist asks: SMACT extends the model rather than reimplementing it, in two directions that only make sense once the workflow is structure-free — substitution tables replaceable by learned, oxidation-state-aware species embeddings, and ranking by selectivity between competing host sites rather than raw probability alone. pymatgen remains a dependency for structure handling and I/O.

Statement of Need gains one sentence on how the four stages compose and where structural cost first enters.

## Notes

- Paper body is now roughly 1,410 words by a plain word count, up from editorialbot's reported 1,257. Still within what JOSS accepts, but worth a look if @crispppp's "quality of writing" concern is partly about length — the Author Contributions section is the largest block and I have not touched it.
- No changes to `paper.bib`; every citation added (`@Hautier2011`, `@Onwuli2024`) was already present.
- `prettier` owns `joss/paper.md` and normalised one emphasis marker (`*composition*` → `_composition_`); otherwise the prose is as written.
- Full suite: 280 passed, 2 skipped. `pre-commit run --all-files` clean apart from the pre-existing `pyright` missing-import errors for the optional `torch`/`aviary` extras.

Once this is on `master`, `@editorialbot generate pdf` will refresh the proof in the review thread.

<!-- This is an auto-generated comment: release notes by coderabbit.ai -->
## Summary by CodeRabbit

* **Documentation**
  * Clarified that only structure prediction requires structural input, using parent structures for substitutions.
  * Documented sign-preserving n-type and p-type dopant criteria.
  * Explained scoring through substitution data or species embeddings, including cation-site selectivity and fixed selectivity of 1.0 for anion substitutions.
  * Documented composition-only usage, `to_table`, and descriptive keys returned by dopant predictions.
  * Added cross-references to Python and pymatgen documentation.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5b40d8215365`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
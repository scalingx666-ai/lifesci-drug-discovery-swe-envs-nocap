# Issue

**Title:** Document data model fields in Field(description=...), starting with constraints

## Description

## Why

BoFire is configured entirely through its pydantic data models, which makes those models the API surface for users and for LLM agents alike. That surface was undocumented in the place that matters:

| | before |
|---|---:|
| data model classes | 245 |
| fields declared on them | 465 |
| fields with `Field(description=...)` | **14** |
| classes with a docstring | 123 |

Only `Field(description=...)` reaches `model_json_schema()`, which is what an agent reads. Prose that did exist sat in Google `Attributes:` blocks — invisible to the schema, and free to drift from the fields it describes.

This PR establishes the convention, installs a ratchet so the gap cannot grow, and migrates one package as the pilot. The remaining 14 packages follow as independent PRs.

## The convention

- Field prose goes in `Field(description=...)`, never an `Attributes:` block.
- The class docstring says what the model is and **when to pick it over its siblings in the union** — the part no generated table can supply.
- `Examples:` blocks are encouraged on concrete types, but optional and not executed (no doctest config is added).
- The `type` discriminator is exempt; it is self-documenting.

Written into `CLAUDE.md` (Code Style, a new "Documentation Ratchet" section, and both data-model checklists) and `CONTRIBUTING.md`.

## The ratchet

`tests/bofire/data_models/test_documentation.py` enumerates all **245** models by walking `bofire.data_models` with `pkgutil`, so a new package is covered the moment it exists. Import errors are deliberately uncaught — a module that fails to import would otherwise drop out of the parametrization and leave a whole package silently unenforced.

Two details worth review:

- It checks **own** fields (those in `cls.__annotations__`), not all of `cls.model_fields`. Without this, one undocumented field on `Strategy` fails all 56 strategy subclasses and the allowlist grows from ~450 entries to thousands.
- The two `UNDOCUMENTED_*` sets record what predates the convention and **may only shrink**. `test_field_allowlist_has_no_stale_entries` and its class counterpart fail once an entry is documented (or removed) without being deleted here, so documenting a package and pruning its entries happen in the same commit.

Seeded at **430 fields / 120 classes** — down from 451/122 by the constraints work in this PR. `git diff` on that file is the migration progress bar.

## The pilot: `constraints`

21 classes, 21 fields, **zero allowlist entries left**. 17 descriptions harvested from `Attributes:` blocks (all blocks removed), 4 written new (`Constraint.features`, `Constraint.context`, `InterpointEqualityConstraint.features`, `NonlinearConstraint.hessian_expression`), and docstrings added to `EqualityConstraint` and `InequalityConstraint`.

One rule surfaced that will apply to every later package: **prose for an inherited field is dropped, not moved.** `NChooseKConstraint` and `NonlinearConstraint` each documented `features` — a field owned by `Constraint` — with different wording. Both were dropped in favour of one canonical description on the base, which now propagates into every constraint's schema.

## Verification

- `pytest tests/bofire/data_models` — 1856 passed, 4 skipped
- `pytest tests/bofire -k constraint` — 240 passed, 9 skipped (repo-wide, includes the strategy and DoE consumers)
- ruff 0.6.5 (the pinned pre-commit version) — clean
- `ty==0.0.16` — 151 diagnostics before and after, i.e. none introduced
- The ratchet was mutation-tested rather than trusted on a green run: a new class with a bare field fails, a class without a docstring fails, and both stale-entry tests fire when an allowlisted entry is documented without being pruned.

Descriptions do not affect `model_dump()`, so the serialization roundtrip contract in `tests/bofire/data_models/serialization/` is untouched.

## Two things reviewers should know

**Nothing changes on the website yet.** quartodoc drops pydantic fields entirely — it renders `DemoModel()` and only whatever sits in an `Attributes:` block. Making these descriptions visible needs a griffe extension wired into the docs build, which is separate work. Removing the `Attributes:` blocks therefore *reduces* rendered output in the short term; the content is in the JSON schema instead.

**`bofire.data_models.domain.constraints.Constraints`** (the container) is still allowlisted. It lives in the `domain` package and belongs to that PR, not this one.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ecfe29396ec7`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
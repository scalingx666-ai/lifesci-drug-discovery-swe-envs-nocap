# Issue

**Title:** #3863 – canonicalSmiles() fails with "SMILES saver: bad cycle number: 100" for highly cyclic valid SMILES

## Description

.

`canonicalSmiles()` can require more than 99 ring closure labels for highly cyclic molecules, even when the same molecule can be serialized successfully with `smiles()`. `SmilesSaver` previously rejected ring closure numbers above 99, causing canonical SMILES generation to fail with `bad cycle number: 100`.

This change adds support for extended ring closure numbers using the `%(n)` form. Existing output remains unchanged for ring closure numbers below 100:

* `1`–`9` continue to use the single-digit form.
* `10`–`99` continue to use the existing `%nn` form.
* `100` and above use `%(n)`.

The %(n) notation is also supported by RDKit and specified by IUPAC SMILES+ for extended ring closure numbers, rather than being an Indigo-specific representation or a Daylight SMILES representation.
https://www.rdkit.org/docs/RDKit_Book.html#ring-closures

The SMILES loader is updated to read the same extended form so generated SMILES can be parsed and round-tripped correctly.

A regression test covers PubChem CID 20652954 from #3863. It verifies the molecule loads with the expected 231 atoms and 430 bonds, canonical SMILES generation succeeds, the resulting extended ring closure syntax can be parsed again, and both ordinary and canonical SMILES round-trip to the same canonical representation.

Existing canonical SMILES regression tests continue to pass unchanged.

This PR was authored using AI.

## Generic request

* [x] PR name follows the pattern `#1234 – issue name`
* [x] branch name does not contain '#'
* [x] base branch (master or release/xx) is correct
* [x] PR is linked with the issue
* [ ] task status changed to "Code review"
* [x] code follows product standards
* [x] regression tests updated

### Optional

* [ ] unit-tests written
* [ ] documentation updated

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `8642d73cca2b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
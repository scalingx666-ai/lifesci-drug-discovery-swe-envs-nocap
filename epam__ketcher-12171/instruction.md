# Issue

**Title:** #4321 - FASTA: Kindly add warning about lost some information while w…

## Description

**Title**: #4321 – FASTA: Show error when saving a mix of RNA and DNA sequences                                                                                                                                                                                     

When the Macromolecules canvas contained both RNA and DNA sequences and the user tried to save to FASTA format, the export silently succeeded, merging both sequence types into a single letter-code string (e.g. AAATTTAAATTT) with no indication that the RNA/DNA distinction was irreversibly lost.

Expected behavior (per requirements): saving a mixed RNA+DNA canvas to FASTA should display the error "Error during sequence type recognition(RNA, DNA or Peptide)".

**Root Cause**
All nucleotide-related monomers — both RNA and DNA — share classHELM = "RNA" in the monomer library, which means monomerItem.props.MonomerType is "RNA" for every component of both sequence types. The existing pre-flight check in validateIfApplicableForFasta() used a Set of MonomerType values to detect mixed content; because both types added the same value, the set never grew beyond size 1, so the validation always passed for RNA+DNA mixes.

**Changes**

_packages/ketcher-core/src/domain/entities/DrawingEntitiesManager.ts_

Added a new public method hasRnaAndDnaMix() that correctly distinguishes RNA from DNA by inspecting:
- Split nucleotides (Sugar instances): monomerItem.label === 'R' (RNA) vs 'dR' (DNA)
- Unsplit nucleotides (UnsplitNucleotide instances): monomerItem.props.MonomerClass === KetMonomerClass.RNA vs KetMonomerClass.DNA

The method is intentionally separate from validateIfApplicableForFasta() because some formats (e.g. IDT) can represent mixed RNA/DNA sequences and must not be blocked by this check.

_packages/ketcher-macromolecules/src/components/modal/save/Save.tsx_

After the existing generic validation, added a FASTA-specific guard that calls hasRnaAndDnaMix() and throws the sequence-type recognition error if the canvas contains both RNA and DNA. IDT and Sequence formats are unaffected.

_packages/ketcher-core/dist/domain/entities/DrawingEntitiesManager.d.ts_

Added hasRnaAndDnaMix(): boolean to the pre-built declaration file so that ketcher-macromolecules (which consumes compiled .d.ts artifacts from ketcher-core/dist) resolves the new method without requiring a full package rebuild.

**Test Changes**

_ketcher-autotests/tests/specs/Macromolecule-editor/Import-Saving-Files/import-saving-fasta.spec.ts_

- Added a new E2E test: "Should not convert .ket file with mixed RNA and DNA to .fasta format and show error" — loads KET/dna-rna-separate.ket (which contains both dR and R sugars) and asserts the error modal shows the expected message.
- Updated the pre-existing test "Saving ambiguous (common) bases (with mapping, mixed) in FASTA format": the fixture for that test also contains mixed RNA/DNA sugars, so with the bug fixed the pre-flight check now fires before Indigo is called. The expected error was updated from the Indigo-level "Can't save '%' to sequence format" to "Error during sequence type recognition(RNA, DNA or Peptide)", and the @IncorrectResultBecauseOfBug tag was removed since the behavior is now correct.



## Check list
- [ ] unit-tests written
- [x] e2e-tests written
- [ ] documentation updated
- [x] PR name follows the pattern `#1234 – issue name`
- [x] branch name doesn't contain '#'
- [x] PR is linked with the issue
- [x] base branch (master or release/xx) is correct
- [x] task status changed to "Code review"
- [x] reviewers are notified about the pull request

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5065e12f00e7`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
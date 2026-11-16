# Issue

**Title:** Add safe handing of max filename length

## Description

## Description
If a filename / path from the qcschema wrapper is too long, an otherwise fine calculation fails.

Example error:
```
Traceback (most recent call last):
  File "/opt/conda/envs/qcfractal/lib/python3.13/site-packages/psi4/driver/schema_wrapper.py", line 565, in run_qcschema
    ret_data = run_json_qcschema(input_model.model_dump(), clean, False, keep_wfn=keep_wfn)
  File "/opt/conda/envs/qcfractal/lib/python3.13/site-packages/psi4/driver/schema_wrapper.py", line 803, in run_json_qcschema
    result_data["native_files"] = {fl: flpath.read_text() for fl, flpath in files.items() if flpath.exists()}
                                                                                             ~~~~~~~~~~~~~^^
  File "/opt/conda/envs/qcfractal/lib/python3.13/pathlib/_abc.py", line 450, in exists
    self.stat(follow_symlinks=follow_symlinks)
    ~~~~~~~~~^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "/opt/conda/envs/qcfractal/lib/python3.13/pathlib/_local.py", line 515, in stat
    return os.stat(self, follow_symlinks=follow_symlinks)
           ~~~~~~~^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
OSError: [Errno 36] File name too long: '/scratch/XXX/YYY/qccompute-19787721/tmpigheoy0f_psi_scratch/24db3d7e-2a5b-4e0d-aed6-e311979e23a2.Zn_3_12_penta_bi_capped_pyramidal_ammonia|D_ammonia|D_hydrogen sulfide|D_hydrogen sulfide|D_hydrogen sulfide|D_hydrogen sulfide|D_hydrogen sulfide|D_methyl|D_methyl|D_methyl|D_methyl|D_phosphine|D.3448022.molden_normal_modes'
```

## User API & Changelog headlines
- [X] If schema wrapper creates a really long file name, or the temp dir has a long path, a calculation won't fail.

## Dev notes & details
- [X] Add utility for "safe" file write, where the proposed path is checked against the OS max and is adjusted by truncating the filename and adding a short hash based on the full filename/path to ensure that it is unique. If the file path is the issue, then the filesystem error is allowed to take place.

## Questions
- [X] Any thoughts? Are updated docs/tests needed?

## AI
- [X] AI was used to process the error and propose an initial solution to which I prodded for better coverage and edited for tight code quality.

## Checklist
- [ ] Tests added for any new features
- [ ] Docstring or narrative docs/sphinxman/source updated if needed
- Test running is well covered by CI. For running locally, see [All or relevant fraction of full tests run](http://psicode.org/psi4manual/master/build_planning.html#how-to-run-a-subset-of-tests)

## Status
- [ ] Ready for review
- Ready for merge -- use Draft/Open GitHub status to signal your view on merge readiness

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f7fb693e70f1`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
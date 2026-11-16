# Issue

**Title:** catch dropped atoms early again

## Description

So some of the performance improvements (https://github.com/MolSSI/QCElemental/blame/master/qcelemental/molparse/from_schema.py#L162) resulted in the admittedly contrived psi4 test case https://github.com/psi4/psi4/blob/master/tests/json/schema-1-throws/input.py#L42 not getting caught at "dropped atoms!" in `contiguize_from_fragment_pattern` but instead later in `from_arrays`.

This PR adds back the test to the ordered case and heals the psi4 test without further downstream changes. Alternatively, we could just alter the text checking for error in the psi4 test.

tracebacks below:

Old behavior (psi4 test passes):
```
	JSON Failure......................................................PASSED
	Contiguous Fragment Error.........................................PASSED
	JSON Failure......................................................PASSED
{'driver': 'energy',
 'error': {'error_message': 'Traceback (most recent call last):\n'
                            '  File '
                            '"/home/psilocaluser/gits/hrw-patch/objdir4/stage/lib/psi4/driver/json_wrapper.py", '
                            'line 217, in run_json\n'
                            '    json_data = '
                            'run_json_qcschema(copy.deepcopy(json_data), '
                            'clean)\n'
                            '  File '
                            '"/home/psilocaluser/gits/hrw-patch/objdir4/stage/lib/psi4/driver/json_wrapper.py", '
                            'line 286, in run_json_qcschema\n'
                            '    mol = core.Molecule.from_schema(molschemus)\n'
                            '  File '
                            '"/home/psilocaluser/gits/hrw-patch/objdir4/stage/lib/psi4/driver/molutil.py", '
                            'line 200, in molecule_from_schema\n'
                            '    molrec = qcel.molparse.from_schema(molschema, '
                            'verbose=verbose)\n'
                            '  File '
                            '"/home/psilocaluser/gits/hrw-patch/objdir4/stage/lib/qcelemental/molparse/from_schema.py", '
                            'line 48, in from_schema\n'
                            '    throw_reorder=True)\n'
                            '  File '
                            '"/home/psilocaluser/gits/hrw-patch/objdir4/stage/lib/qcelemental/molparse/from_schema.py", '
                            'line 146, in contiguize_from_fragment_pattern\n'
                            '    raise ValidationError("""dropped atoms! nat = '
                            '{} != {}""".format(nat, ncgeom.shape[0]))\n'
                            'qcelemental.exceptions.ValidationError: dropped '
                            'atoms! nat = 2 != 3\n',
           'error_type': 'ValidationError'},
 'keywords': {'scf_type': 'df'},
 'model': {'basis': 'cc-pVDZ', 'method': 'SCF'},
 'molecule': {'geometry': [0.0,
                           0.0,
                           -0.1294769411935893,
                           0.0,
                           -1.494187339479985,
                           1.0274465079245698,
                           0.0,
                           1.494187339479985,
                           1.0274465079245698],
              'symbols': ['O', 'H']},
 'raw_output': '',
 'schema_name': 'qc_schema_input',
 'schema_version': 1,
 'success': False}
	Symbol Error......................................................PASSED
	JSON Failure......................................................PASSED
	Keyword Error.....................................................PASSED
```

Current behavior (test fails)
```
Warning: QCElemental is reordering atoms to accommodate non-contiguous fragments
    JSON Failure......................................................PASSED
    Contiguous Fragment Error.........................................PASSED
    JSON Failure......................................................PASSED
{'driver': 'energy',
 'error': {'error_message': 'Traceback (most recent call last):\n'
                            '  File '
                            '"/home/psilocaluser/gits/hrw-quaternary/objdir37b/stage/lib/psi4/driver/json_wrapper.py", '
                            'line 217, in run_json\n'
                            '    json_data = '
                            'run_json_qcschema(copy.deepcopy(json_data), '
                            'clean)\n'
                            '  File '
                            '"/home/psilocaluser/gits/hrw-quaternary/objdir37b/stage/lib/psi4/driver/json_wrapper.py", '
                            'line 286, in run_json_qcschema\n'
                            '    mol = core.Molecule.from_schema(molschemus)\n'
                            '  File '
                            '"/home/psilocaluser/gits/hrw-quaternary/objdir37b/stage/lib/psi4/driver/molutil.py", '
                            'line 200, in molecule_from_schema\n'
                            '    molrec = qcel.molparse.from_schema(molschema, '
                            'verbose=verbose)\n'
                            '  File '
                            '"/home/psilocaluser/gits/qcelemental/qcelemental/molparse/from_schema.py", '
                            'line 49, in from_schema\n'
                            '    throw_reorder=True)\n'
                            '  File '
                            '"/home/psilocaluser/gits/qcelemental/qcelemental/molparse/from_schema.py", '
                            'line 146, in contiguize_from_fragment_pattern\n'
                            '    print(geom.shape())\n'
                            "AttributeError: 'list' object has no attribute "
                            "'shape'\n",
           'error_type': 'AttributeError'},
 'keywords': {'scf_type': 'df'},
 'model': {'basis': 'cc-pVDZ', 'method': 'SCF'},
 'molecule': {'geometry': [0.0,
                           0.0,
                           -0.1294769411935893,
                           0.0,
                           -1.494187339479985,
                           1.0274465079245698,
                           0.0,
                           1.494187339479985,
                           1.0274465079245698],
              'symbols': ['O', 'H']},
 'raw_output': '',
 'schema_name': 'qc_schema_input',
 'schema_version': 1,
 'success': False}
    Symbol Error......................................................FAILED
```

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `7cb0fc8f8454`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
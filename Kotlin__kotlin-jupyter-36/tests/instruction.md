# Issue

**Title:** Fix file extension in language_info

## Description

Currently trying to use nbconvert to script on Notebooks with a Kotlin kernel fails with the error below. This pull request fixes this.

```
$ jupyter nbconvert ktnotebook.ipynb --to script
[NbConvertApp] Converting notebook day01kt.ipynb to script
Traceback (most recent call last):
  File "/home/mpcjanssen/.local/bin/jupyter-nbconvert", line 11, in <module>
    sys.exit(main())
  File "/home/mpcjanssen/.local/lib/python3.6/site-packages/jupyter_core/application.py", line 268, in launch_instance
    return super(JupyterApp, cls).launch_instance(argv=argv, **kwargs)
  File "/home/mpcjanssen/.local/lib/python3.6/site-packages/traitlets/config/application.py", line 664, in launch_instance
    app.start()
  File "/home/mpcjanssen/.local/lib/python3.6/site-packages/nbconvert/nbconvertapp.py", line 340, in start
    self.convert_notebooks()
  File "/home/mpcjanssen/.local/lib/python3.6/site-packages/nbconvert/nbconvertapp.py", line 510, in convert_notebooks
    self.convert_single_notebook(notebook_filename)
  File "/home/mpcjanssen/.local/lib/python3.6/site-packages/nbconvert/nbconvertapp.py", line 481, in convert_single_notebook
    output, resources = self.export_single_notebook(notebook_filename, resources, input_buffer=input_buffer)
  File "/home/mpcjanssen/.local/lib/python3.6/site-packages/nbconvert/nbconvertapp.py", line 410, in export_single_notebook
    output, resources = self.exporter.from_filename(notebook_filename, resources=resources)
  File "/home/mpcjanssen/.local/lib/python3.6/site-packages/nbconvert/exporters/exporter.py", line 179, in from_filename
    return self.from_file(f, resources=resources, **kw)
  File "/home/mpcjanssen/.local/lib/python3.6/site-packages/nbconvert/exporters/exporter.py", line 197, in from_file
    return self.from_notebook_node(nbformat.read(file_stream, as_version=4), resources=resources, **kw)
  File "/home/mpcjanssen/.local/lib/python3.6/site-packages/nbconvert/exporters/script.py", line 63, in from_notebook_node
    self.file_extension = langinfo.get('file_extension', '.txt')
  File "/home/mpcjanssen/.local/lib/python3.6/site-packages/traitlets/traitlets.py", line 585, in __set__
    self.set(obj, value)
  File "/home/mpcjanssen/.local/lib/python3.6/site-packages/traitlets/traitlets.py", line 559, in set
    new_value = self._validate(obj, value)
  File "/home/mpcjanssen/.local/lib/python3.6/site-packages/traitlets/traitlets.py", line 591, in _validate
    value = self.validate(obj, value)
  File "/home/mpcjanssen/.local/lib/python3.6/site-packages/nbconvert/exporters/exporter.py", line 43, in validate
    raise TraitError(msg.format(self.name, value))
traitlets.traitlets.TraitError: FileExtension trait 'file_extension' does not begin with a dot: 'kt'
```

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6d977779312e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
# Issue

**Title:** Update fulqrum dependency to have version bound

## Description

The 0.13.0 release failed to publish to pypi because fulqrum was specified as a direct reference:

```
Uploading distributions to https://upload.pypi.org/legacy/
  INFO     dist/qiskit_addon_sqd-0.13.0-py3-none-any.whl (36.1 KB)
  INFO     dist/qiskit_addon_sqd-0.13.0.tar.gz (459.8 KB)
  INFO     username set by command options
  INFO     password set by command options
  INFO     username: __token__
  INFO     password: <hidden>
  Uploading qiskit_addon_sqd-0.13.0-py3-none-any.whl
  INFO     Response from https://upload.pypi.org/legacy/:
           400 Bad Request
  INFO     <html>
            <head>
             <title>400 Can't have direct dependency: fulqrum @
           git+https://github.com/qiskit-community/fulqrum.git@dafb4091d552d130c42
           d13dc74a3484e12d70d3f ; extra == "dev". See
           https://packaging.python.org/specifications/core-metadata for more
           information.</title>
            </head>
            <body>
             <h1>400 Can't have direct dependency: fulqrum @
           git+https://github.com/qiskit-community/fulqrum.git@dafb4091d552d130c42
           d13dc74a3484e12d70d3f ; extra == "dev". See
           https://packaging.python.org/specifications/core-metadata for more
           information.</h1>
             The server could not comply with the request since it is either
           malformed or otherwise incorrect.<br/><br/>
           Can&#x27;t have direct dependency: fulqrum @
           git+https://github.com/qiskit-community/fulqrum.git@dafb4091d552d130c42
           d13dc74a3484e12d70d3f ; extra == &quot;dev&quot;. See
           https://packaging.python.org/specifications/core-metadata for more
           information.

            </body>
           </html>
  ERROR    HTTPError: 400 Bad Request from https://upload.pypi.org/legacy/
           Bad Request
```

This issue happened because #305 was merged prematurely, before  was fully addressed.

In order to make a working release, this PR will need to be merged before the 0.14.0 release of this package.

However, this change is on hold until fulqrum is released to pypi.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d04d44adfce1`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
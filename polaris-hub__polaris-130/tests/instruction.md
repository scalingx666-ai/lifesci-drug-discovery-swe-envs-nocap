# Issue

**Title:** Fix auth token being `None` during login

## Description

## Changelogs

- Fix a bug in the login flow where `self.token` was expected to be an `OAuth2Token` instance, but was `None`

---

_Checklist:_

- [ ] ~_Was this PR discussed in an issue? It is recommended to first discuss a new feature into a GitHub issue before opening a PR._~
- [ ] ~_Add tests to cover the fixed bug(s) or the newly introduced feature(s) (if appropriate)._~
- [ ] ~_Update the API documentation if a new function is added, or an existing one is deleted._~
- [X] _Write concise and explanatory changelogs above._
- [X] _If possible, assign one of the following labels to the PR: `feature`, `fix`, `chore`, `documentation` or `test` (or ask a maintainer to do it for you)._

---

For future reference, this would lead to the following stack-trace: 
```
(polaris) ➜  polaris git:(feat/zarr-checksum) _TYPER_STANDARD_TRACEBACK=1 polaris login --overwrite
Traceback (most recent call last):
  File "/Users/cas.wognum/micromamba/envs/polaris/bin/polaris", line 8, in <module>
    sys.exit(app())
             ^^^^^
  File "/Users/cas.wognum/micromamba/envs/polaris/lib/python3.12/site-packages/typer/main.py", line 326, in __call__
    raise e
  File "/Users/cas.wognum/micromamba/envs/polaris/lib/python3.12/site-packages/typer/main.py", line 309, in __call__
    return get_command(self)(*args, **kwargs)
           ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "/Users/cas.wognum/micromamba/envs/polaris/lib/python3.12/site-packages/click/core.py", line 1157, in __call__
    return self.main(*args, **kwargs)
           ^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "/Users/cas.wognum/micromamba/envs/polaris/lib/python3.12/site-packages/typer/core.py", line 723, in main
    return _main(
           ^^^^^^
  File "/Users/cas.wognum/micromamba/envs/polaris/lib/python3.12/site-packages/typer/core.py", line 193, in _main
    rv = self.invoke(ctx)
         ^^^^^^^^^^^^^^^^
  File "/Users/cas.wognum/micromamba/envs/polaris/lib/python3.12/site-packages/click/core.py", line 1688, in invoke
    return _process_result(sub_ctx.command.invoke(sub_ctx))
                           ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "/Users/cas.wognum/micromamba/envs/polaris/lib/python3.12/site-packages/click/core.py", line 1434, in invoke
    return ctx.invoke(self.callback, **ctx.params)
           ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "/Users/cas.wognum/micromamba/envs/polaris/lib/python3.12/site-packages/click/core.py", line 783, in invoke
    return __callback(*args, **kwargs)
           ^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "/Users/cas.wognum/micromamba/envs/polaris/lib/python3.12/site-packages/typer/main.py", line 692, in wrapper
    return callback(**use_params)
           ^^^^^^^^^^^^^^^^^^^^^^
  File "/Users/cas.wognum/Documents/repositories/polaris/polaris/cli.py", line 31, in login
    client.login(auto_open_browser=auto_open_browser, overwrite=overwrite)
  File "/Users/cas.wognum/Documents/repositories/polaris/polaris/hub/client.py", line 220, in login
    token_is_valid = self.ensure_active_token(self.token)
                     ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "/Users/cas.wognum/Documents/repositories/polaris/polaris/hub/client.py", line 137, in ensure_active_token
    is_active = super().ensure_active_token(token)
                ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "/Users/cas.wognum/micromamba/envs/polaris/lib/python3.12/site-packages/authlib/oauth2/client.py", line 261, in ensure_active_token
    if not token.is_expired():
           ^^^^^^^^^^^^^^^^
AttributeError: 'NoneType' object has no attribute 'is_expired'
```

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6404029ea4e8`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
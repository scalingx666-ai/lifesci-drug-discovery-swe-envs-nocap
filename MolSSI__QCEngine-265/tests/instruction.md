# Issue

**Title:** Add XTB to the standard suite of harnesses

## Description

## Description
Fixes the XTB harness to ensure any data in extra fields are preserved.

Otherwise, we see the following error when completed XTB tasks are sent to QCFractal.

```
[E 200828 14:44:49 web:1792] Uncaught exception POST /queue_manager (::1)
    HTTPServerRequest(protocol='https', host='localhost:7874', method='POST', uri='/queue_manager', version='HTTP/1.1', remote_ip='::1')
    Traceback (most recent call last):
      File "/lus/theta-fs0/projects/CSC249ADCD08/qcarchive/env/lib/python3.7/site-packages/tornado/web.py", line 1701, in _execute
        result = method(*self.path_args, **self.path_kwargs)
      File "/lus/theta-fs0/projects/CSC249ADCD08/qcarchive/src/QCFractal/qcfractal/queue/handlers.py", line 285, in post
        success, error = self.insert_complete_tasks(self.storage, body.data, self.logger)
      File "/lus/theta-fs0/projects/CSC249ADCD08/qcarchive/src/QCFractal/qcfractal/queue/handlers.py", line 234, in insert_complete_tasks
        com, err, hks = procedure_parser.parse_output(v)
      File "/lus/theta-fs0/projects/CSC249ADCD08/qcarchive/src/QCFractal/qcfractal/procedures/procedures.py", line 369, in parse_output
        results = parse_single_tasks(self.storage, traj_dict)
      File "/lus/theta-fs0/projects/CSC249ADCD08/qcarchive/src/QCFractal/qcfractal/procedures/procedures_util.py", line 115, in parse_single_tasks
        v["keywords"] = v["extras"]["_qcfractal_tags"]["keywords"]
    KeyError: '_qcfractal_tags'

```

## Changelog description
Bug fix: Ensure extra tags are preserved in XTB harness

## Status
<!-- Please `pip install .[lint]; make format` in the base folder. -->
- [x] Code base linted
- [x] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ff693c467285`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
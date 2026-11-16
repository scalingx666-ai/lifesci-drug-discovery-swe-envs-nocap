# Issue

**Title:** Probably fix flaky snowflake test

## Description

## Description
<!-- Provide a brief description of the PR's purpose here. -->

@bennybp spotted a very plausible reason for why one of our snowflake CI tests has always been flaky. Has nothing to do with QCFractal and has been around for 13y. Credit also to @JonathonMisiewicz who reported LCCSD showing up in the error for an otherwise CCSD test. Such errors shouldn't be widespread b/c stdsuite tests for unexpectedly present qcvars, but lccsd isn't in stdsuite :-(

## User API & Changelog headlines
<!-- A bullet-point format description of how this PR affects the user.
     This is destined for the release notes. May be empty. -->
- [x] fix oughtn't to be set qcvars for local CC methods


```
=================================== FAILURES ===================================
_________________ test_cbs_with_managed_conditions[snowflake] __________________
[gw0] linux -- Python 3.13.11 /usr/share/miniconda/envs/p4build/bin/python3.13

distributed = True
snowflake = <qcfractal.snowflake.FractalSnowflake object at 0x7f947bed8c20>

    @pytest.mark.cbs
    @pytest.mark.parametrize("distributed", [
        pytest.param(False, id="internal"),
        pytest.param(True,  id="snowflake", marks=using("qcfractal")),
    ])
    def test_cbs_with_managed_conditions(distributed, snowflake):
    
        n = psi4.geometry("""
                0 4
                N 0.00 0.00 0.00
            """)
    
        psi4.set_options({
            "scf_type": "direct",
            "reference": "rohf",
            "r_convergence": 6,
            "d_convergence": 7,
            "e_convergence": 8,
            "freeze_core": True,
        })
    
        cmd_kwargs = {
            "scf_basis": "aug-cc-pV[TQ5]Z",
            "corl_wfn": "mp2",
            "corl_basis": "aug-cc-pV[TQ]Z",
            "delta_wfn": "ccsd(t)",
            "delta_basis": "aug-cc-pV[DT]Z",
        }
    
        if distributed:
            client = snowflake.client()
            plan = psi4.energy("cbs", **cmd_kwargs, return_plan=True)
            plan.compute(client)
            snowflake.await_results()
>           e_cbs = plan.get_psi_results(client)
                    ^^^^^^^^^^^^^^^^^^^^^^^^^^^^

/home/runner/work/psi4/psi4/objdir/stage/lib/psi4/tests/test_composite.py:64: 
_ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ 
/home/runner/work/psi4/psi4/objdir/stage/lib/psi4/driver/driver_cbs.py:1797: in get_psi_results
    cbs_model = self.get_results(client=client)
                ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
/home/runner/work/psi4/psi4/objdir/stage/lib/psi4/driver/driver_cbs.py:1698: in get_results
    assembled_results = self._prepare_results(client=client)
                        ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
_ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ 

self = CompositeComputer(molecule=<psi4.core.Molecule object at 0x7f947a4539b0>, basis='(auto)', method='cbs', driver=<Driver...q]z', delta_wfn='ccsd(t)', return_plan=True, delta_basis='aug-cc-pv[dt]z', scf_basis='aug-cc-pv[tq5]z', corl_wfn='mp2')
client = PortalClient(server_name='QCFractal Server', address='http://localhost:44257/', username='None')

    def _prepare_results(self, client: Optional["qcportal.client.PortalClient"] = None):
        results_list = [x.get_results(client=client) for x in self.task_list]
    
>       modules = [getattr(v.provenance, "module", None) for v in results_list]
                           ^^^^^^^^^^^^
E       AttributeError: 'dict' object has no attribute 'provenance'

/home/runner/work/psi4/psi4/objdir/stage/lib/psi4/driver/driver_cbs.py:1631: AttributeError
------------------------------ Captured log call -------------------------------
INFO     psi4.driver.task_planner:task_planner.py:239 PLANNING CBS:  packet={packet} kw={kwargs}
INFO     psi4.driver.driver_cbs:driver_cbs.py:1362 
  //>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>//
  //             CBS Setup             //
  //<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<//

    Naive listing of computations required.
             hf / aug-cc-pvtz              for  HF TOTAL ENERGY
             hf / aug-cc-pvqz              for  HF TOTAL ENERGY
             hf / aug-cc-pv5z              for  HF TOTAL ENERGY
            mp2 / aug-cc-pvtz              for  MP2 TOTAL ENERGY
            mp2 / aug-cc-pvqz              for  MP2 TOTAL ENERGY
        ccsd(t) / aug-cc-pvdz              for  CCSD(T) TOTAL ENERGY
        ccsd(t) / aug-cc-pvtz              for  CCSD(T) TOTAL ENERGY
            mp2 / aug-cc-pvdz              for  MP2 TOTAL ENERGY

    Enlightened listing of computations required.
             hf / aug-cc-pv5z              for  HF TOTAL ENERGY
            mp2 / aug-cc-pvqz              for  MP2 TOTAL ENERGY
        ccsd(t) / aug-cc-pvdz              for  CCSD(T) TOTAL ENERGY
        ccsd(t) / aug-cc-pvtz              for  CCSD(T) TOTAL ENERGY

    Full listing of computations to be obtained (required and bonus).
             hf / aug-cc-pv5z              for  HF TOTAL ENERGY
             hf / aug-cc-pvqz              for  HF TOTAL ENERGY
            mp2 / aug-cc-pvqz              for  MP2 TOTAL ENERGY
             hf / aug-cc-pvdz              for  HF TOTAL ENERGY
            mp2 / aug-cc-pvdz              for  MP2 TOTAL ENERGY
           ccsd / aug-cc-pvdz              for  CCSD TOTAL ENERGY
        ccsd(t) / aug-cc-pvdz              for  CCSD(T) TOTAL ENERGY
             hf / aug-cc-pvtz              for  HF TOTAL ENERGY
            mp2 / aug-cc-pvtz              for  MP2 TOTAL ENERGY
           ccsd / aug-cc-pvtz              for  CCSD TOTAL ENERGY
        ccsd(t) / aug-cc-pvtz              for  CCSD(T) TOTAL ENERGY

ERROR    qcfractal.components.tasks.socket:socket.py:201 Internal FractalServer Error:
Traceback (most recent call last):
  File "/usr/share/miniconda/envs/p4build/lib/python3.13/site-packages/sqlalchemy/engine/base.py", line 1967, in _exec_single_context

...
  File "/usr/share/miniconda/envs/p4build/lib/python3.13/site-packages/sqlalchemy/engine/default.py", line 952, in do_execute
    cursor.execute(statement, parameters)
    ~~~~~~~~~~~~~~^^^^^^^^^^^^^^^^^^^^^^^
sqlalchemy.exc.DataError: (psycopg2.errors.InvalidTextRepresentation) invalid input syntax for type json
LINE 1: ...1T16:45:22.913508+00:00'::timestamptz, properties='{"return_...
                                                             ^
DETAIL:  Token "NaN" is invalid.
CONTEXT:  JSON data, line 1: ...00048539819838, "lccsd (+lmp2) total energy": NaN...

[SQL: UPDATE base_record SET extras=%(extras)s::JSONB, status=%(status)s, manager_name=%(manager_name)s, modified_on=%(modified_on)s, properties=%(properties)s::JSONB WHERE base_record.id = %(id_1)s]
[parameters: {'extras': '{}', 'status': 'complete', 'manager_name': 'snowflake_compute-runnervmwffz4-2761b6a5-f20e-4f48-9f72-bebba5fe97d5', 'modified_on': datetime.datetime(2026, 2, 11, 16, 45, 22, 913508, tzinfo=datetime.timezone.utc), 'properties': '{"return_result": -54.4869038630141, "(t) correction energy": -0.001301076608982411, "aaa (t) correction energy": -0.00013515271269359542, "aab (t) c ... (2426 characters truncated) ... tions": 11, "ccsd_prt_pr_correlation_energy": -0.09703313392780007, "ccsd_prt_pr_total_energy": -54.4869038630141, "ccsd_prt_pr_dipole_moment": null}', 'id_1': 2}]
```

## Status
- [x] Ready for review
- [x] Ready for merge

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ad16e49ef6cb`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
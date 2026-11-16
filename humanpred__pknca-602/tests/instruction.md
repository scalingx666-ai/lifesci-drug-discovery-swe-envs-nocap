# Issue

**Title:** Only report missing dosing when a requested parameter needs it

## Description

.

pk.nca() reported missing dosing information whenever no PKNCAdose was given, regardless of what was requested, and did not say what the consequence was.  Requesting only cmax and auclast produced the message even though both are calculated from concentrations alone.

Whether a parameter needs dosing is now derived from the registry rather than declared.  A backward walk follows each parameter's formals -- after its formalsmap -- and its declared dependencies until it reaches the inputs pk.nca.interval() supplies directly, and records whether the dose amount, the dose time, or the dose duration is among them.  The three are recorded separately because they are supplied separately: c0 needs the dose time but not the amount, ceoi needs the duration, and cl.last needs the amount. Transitive requirements are caught, so vz.obs is reported through cl.obs.

The walk is deferred to the first pk.nca() call and cached in the registry, because a parameter can be registered before what it depends on (clr.obs refers to aucinf.obs, which is registered later).  Re-registering a parameter clears the cache, since anything downstream of it may change.

pk.calc.half.life() is the one calculation that accepts dose timing without requiring it.  Left unmarked it would report 148 of 203 parameters as uncalculable rather than 109, wrongly including aucinf.obs, lambda.z, mrt.obs, and span.ratio, because the whole terminal-phase family descends from it.  Its signature cannot distinguish this -- pk.calc.half.life's duration.dose and pk.calc.c0's time.dose both default to 0, and only one is optional -- so it is listed in pknca_optional_dose_args.

A test enumerates parameters and compares each derived flag against whether pk.nca() can actually calculate that parameter without dosing, so a wrong flag or a newly added parameter fails rather than producing a wrong message.

Three existing tests asserted the message for aucinf.obs, ctrough, and cmax, none of which need dosing; they now assert its absence.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `686509f9f74b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
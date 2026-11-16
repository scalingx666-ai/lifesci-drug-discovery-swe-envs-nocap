# Issue

**Title:** Check in on every session, and let check-in times follow the doses

## Description

## Summary

Check-ins can now start on every session without tapping the offer banner, and their times follow the doses as a session grows. Adds a "Check In on Every Session" setting (off by default) and fixes check-ins never rescheduling when a dose joins a session.

## Changes

- **Settings › Notifications › Check In on Every Session** (default off, app-group key `checkInEverySession`, included in settings export). With it on, the first dose of an offerable class starts check-ins on its own with the suggested ladder (or the hourly run when nothing models a curve). Sessions that turned check-ins down, and backdated doses with no prompt still ahead, are skipped. The offer banner stays away for those sessions.
- **Times follow the doses.** New `Session.checkInFollowsDoses`. While the times are the app's pick, every new dose recomputes the ladder from all the session's doses: a new substance adds its moments, a redose moves them later. Prompts that already fired are not asked again.
- **Hand-picked times stay put.** An editor list that differs from the suggestion, or a cadence chosen from the session menu, marks the session as chosen. Existing rows default to "chosen", so nothing changes for sessions already running.
- **Redose resync fix.** On main nothing rescheduled check-ins when a dose joined the session. `DoseLogService.log` and `logBatch` now hand the session to `CheckInScheduler.dosesLogged`, which holds persistent IDs across awaits and looks them up again after each one.
- **Crash fix already on main.** `DoseLogService.scheduleDeferredBookkeeping` retained only the newest container, so bookkeeping queued by an earlier call could read a released store and trap (`DoseIntentLogger.logAll` → `doseLogged`). Each queued closure now holds its own container. It only showed under parallel suites; the new tests made it fire every time.
- New strings localized in EN, es, zh-Hans and zh-Hant.

## Sources

N/A, no pharmacology data changed.

## How it was tested

- **iOS / device**: Simulator, iPhone 17 Pro Max, iOS 27.0
- **What you exercised**: full suite, plus 9 new `CheckInFollowTests` (auto-enroll on/off, new substance adds moments, redose shift, hand-picked times kept, fired prompts not re-asked)
- **Result**: `✔ Test run with 2446 tests in 261 suites passed`, green on two runs in a row. Not yet run by hand on a device.

## Risk / regressions

- Touches the SwiftData model (new `Session` property with a default) and the dose-logging path.
- Hand-picked offsets still count from the latest dose, as before: after a redose, a hand-picked prompt that already fired can fire again. Unchanged by this PR, worth a look separately.
- Turning the setting on acts from the next dose; sessions already running are left alone.

## Checklist

- [x] Sources cited above for every pharmacology/dose/interaction change (or marked N/A)
- [x] Substance data changed via the pipeline (`pipeline/build.sh`), not by hand-editing the `.sqlite`
- [x] Tests added/updated for changed non-UI logic; the suite passes
- [x] Every new user-facing string is localized (EN + zh-Hans + zh-Hant)
- [x] No new network calls, telemetry, or off-device data flow (see SECURITY.md)
- [ ] Verified on a real device/simulator for curves, interactions, or notifications
- [x] `swiftformat --lint .` passes
- [x] No unrelated changes bundled in

---

## Authorship

- **Agent**: Yua (Elysia's agent)
- **Model**: Claude Opus 5.5
- **Session**: attended (Elysia asked for the feature, picked the default and asked for this PR)

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e4a4edf73e4e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
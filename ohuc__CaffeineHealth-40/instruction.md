# Issue

**Title:** feature(hydration): log hydration data to HealthConnect

## Description

# Add hydration data sync to Health Connect
When logging a drink (coffee, tea, etc.), the app already syncs the caffeine content to Health Connect as a NutritionRecord. This PR adds an HydrationRecord, so Health Connect also track the user's hydration.

## Changes
- AndroidManifest.xml — Declares the WRITE_HYDRATION permission required by Health Connect
- HealthConnectManager.kt — Adds HydrationRecord write capability alongside the existing NutritionRecord writes. A volumeMl parameter is passed through the call chain. When present and the hydration permission is granted, a HydrationRecord is inserted in the same batch as the NutritionRecord. Deletion also cascades to the associated hydration record. The hydration permission is bundled into the existing allPermissions set so it's requested together with the nutrition permission.
- CaffeineViewModel.kt — Computes the volume (quantity × unit.milliliters) at the three logging call sites that have access to the DrinkUnit data: logDrink(), logDrinkFromAddScreen(), and updateLoggedEntry(). Call sites without unit data (coach dose, recent drink, widget quick-log) pass null — no hydration record is created, which is the expected behavior.

## What it means for users
- The next time they enable Health Connect, a new "Hydration" permission will appear in the grant dialog
- From that point on, every logged drink with a known volume (e.g., 250ml coffee, 330ml can) creates both a caffeine record and a hydration record in Health Connect
- Past entries are not backfilled

## Disclaimer
I used AI assistance to help implement these changes. I am not an experienced Android/Kotlin developer, so please review carefully — especially the Health Connect API usage and permission flow.

## Screenshot
<img width="1024" height="658" alt="hydration_2" src="https://github.com/user-attachments/assets/1546fec4-4d15-4216-bb63-6b89a6aede8a" />

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `78c1e14dbd2a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
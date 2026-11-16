# Issue

**Title:** Switch to Lets-Plot Kotlin API 0.0.18-SNAPSHOT

## Description

Added:
 - Geometries:
   - geom_crossbar()
   - geom_errorbar()
   - geom_freqpoly()
   - geom_linerange()
   - geom_pointrange()
   - geom_polygon()
   - geom_ribbon()
   - geom_step()

 - Standardize input data series as List<*>:
   - Iterable<*>
   - Sequence<*>
   - Array<*>
   - ByteArray
   - ShortArray
   - IntArray
   - LongArray
   - FloatArray
   - DoubleArray
   - CharArray

 - Standardize values in the input data series:
   - Date, Instant and ZonedDateTime as the number of milliseconds from the epoch of 1970-01-01T00:00:00Z.
   - Char as string

Fixed:
 - geom_density:
   - defaults: alpha=0, fill=white
   - support weight aesthetic
 - geom_histogram: added 'bin' parameters: binCount, binWidth, center, boundary.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `bd1eb4b62336`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
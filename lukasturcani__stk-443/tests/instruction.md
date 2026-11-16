# Issue

**Title:** Remove old API from `Complex`

## Description

The `guest`, `guest_start` and other related parameters have
been removed from the initializer of the `Complex` topology graph.
Users were warned about this deprecation a long time ago so this
should not come as a surprise.

The other change is that the `guests` parameter is now no longer
optional. It was only optional so that users could continue to use
the old API, but now that the old API has been removed, the `guests`
parameter will always be required. After all, it would not make sense
to have a host-guest complex without a guest!

The other thing I did was that the type hint now correctly allows users
to provide a single `Guest` instance, rather than just an `Iterable`
of `Guest` instances. This was just an error in the previous type hint.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1160b35e0a0e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
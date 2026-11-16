# Issue

**Title:** Moved cache in message_type serializer to ConcurrentHashMap

## Description

Moved cache in message_type serializer to ConcurrentHashMap to avoid concurrent modification exceptions. ConcurrentHashMap seems a good fit due to low overhead when reading from the map (which is the main purpose of a cache).

Updated both MessageTypeSerializer and DetailsLevelSerializer.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `631f85bbb5d9`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
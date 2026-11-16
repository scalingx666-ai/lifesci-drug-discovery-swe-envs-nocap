# Issue

**Title:** Splunk monitoring including tracking country and use case

## Description

This pull request introduces a new "tracking use case" feature to the `serve` command in the `ersilia` CLI, enhances tracking capabilities in the core model and session modules, and adds functionality for geographic data retrieval. The changes improve the flexibility and granularity of tracking, allowing users to specify use cases and collect additional metadata such as country information.

### Enhancements to the `serve` command:
* Added a new `--tracking-use-case` option to the `serve` command, allowing users to specify tracking contexts such as "local," "self-service," "hosted," or "test." This option integrates with the `track` flag to enable more granular tracking. (`ersilia/cli/commands/serve.py`, [[1]](diffhunk://#diff-bf2cb8d9ea55f818ef68bbb4c3ca35ea81e63f952c2277ca47eefd60b3b08b0eR53-R80) [[2]](diffhunk://#diff-bf2cb8d9ea55f818ef68bbb4c3ca35ea81e63f952c2277ca47eefd60b3b08b0eL90-R110) [[3]](diffhunk://#diff-bf2cb8d9ea55f818ef68bbb4c3ca35ea81e63f952c2277ca47eefd60b3b08b0eL137-R152)
* Updated variable naming for consistency, changing `maxmemory` to `max_memory` throughout the `serve` command. (`ersilia/cli/commands/serve.py`, [[1]](diffhunk://#diff-bf2cb8d9ea55f818ef68bbb4c3ca35ea81e63f952c2277ca47eefd60b3b08b0eR53-R80) [[2]](diffhunk://#diff-bf2cb8d9ea55f818ef68bbb4c3ca35ea81e63f952c2277ca47eefd60b3b08b0eL90-R110)

### Core model tracking improvements:
* Modified the `serve` method in `ersilia/core/model.py` to accept `track_runs` as a string (use case) instead of a boolean, and introduced logic to handle the new tracking use case. (`ersilia/core/model.py`, [[1]](diffhunk://#diff-f11c37b66cae27db19f6186c3c81be9de6e57ef05e4f47be27449806d435290aL650-R650) [[2]](diffhunk://#diff-f11c37b66cae27db19f6186c3c81be9de6e57ef05e4f47be27449806d435290aL660-R668) [[3]](diffhunk://#diff-f11c37b66cae27db19f6186c3c81be9de6e57ef05e4f47be27449806d435290aL676-R688)
* Enhanced the `RunTracker` class to include the `use_case` parameter, which is now incorporated into event data and metadata. (`ersilia/core/tracking.py`, [[1]](diffhunk://#diff-64965392109ab24f59cfd7848c73d61218fa4dc40aacca63b1e9e3a496fba5e4L127-R131) [[2]](diffhunk://#diff-64965392109ab24f59cfd7848c73d61218fa4dc40aacca63b1e9e3a496fba5e4R413-R422)

### Session tracking updates:
* Added methods `register_tracking_use_case` and `get_tracking_use_case` to the `Session` class, enabling the storage and retrieval of tracking use case information in session files. (`ersilia/core/session.py`, [[1]](diffhunk://#diff-dd8374eb1e491690debbe04fe71354ea54d903ac327aeebfd3dfb09bf0f939f3R131-R147) [[2]](diffhunk://#diff-dd8374eb1e491690debbe04fe71354ea54d903ac327aeebfd3dfb09bf0f939f3R165-R181)

### Geographic data retrieval:
* Introduced a `get_country` method in the `SystemChecker` class to determine the user's country based on their IP address, using a bash script and external API calls. This data is included in tracking metadata. (`ersilia/utils/system.py`, [[1]](diffhunk://#diff-ca6d8230f8d390e30e38fb36c3250b583de5c3879854d007d1dc1c58a660b2d3R3-R6) [[2]](diffhunk://#diff-ca6d8230f8d390e30e38fb36c3250b583de5c3879854d007d1dc1c58a660b2d3R82-R143)
* Updated the `RunTracker` class to use the `get_country` method to include geographic data in event summaries. (`ersilia/core/tracking.py`, [[1]](diffhunk://#diff-64965392109ab24f59cfd7848c73d61218fa4dc40aacca63b1e9e3a496fba5e4R346-R366) [[2]](diffhunk://#diff-64965392109ab24f59cfd7848c73d61218fa4dc40aacca63b1e9e3a496fba5e4R413-R422)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f3067bae57e0`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
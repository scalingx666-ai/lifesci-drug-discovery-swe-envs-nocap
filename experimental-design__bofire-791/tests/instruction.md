# Issue

**Title:** Update dependency from pandas to 3.0.0 to implement standardized WriteOnCopy-Behaviour on Pandas Dataframes. Refers to issue #777.

## Description

<!--
Thank you for sending the PR! We appreciate you spending the time to make BoFire better.

Help us to understand your motivation by explaining why you decided to make this change.

You can learn more about contributing to BoFire here: https://github.com/experimental-desgin/bofire/blob/main/CONTRIBUTING.md
-->

## Motivation

In Issue #777 pandas of version prior to 3.0.0 can cause SettingToCopyWarning. In even older pandas version evoking Strategy.tell with a spliced view could change the original dataframe in theory.

To mitigate this we can increase the dependency of pandas to atleast 3.0.0 to implement the standardized CopyOnWrite-Behaviour, where a pandas.Dataframe automaticly delivers a copy (instead of a view) when doing a filter-operation or something similar to it. The SettingWithCopyWarning would also not appear anymore.

I don't believe that would cause any new issues since it would restrict the version and not expand it. Please correct me if I'm wrong.

### Have you read the [Contributing Guidelines on pull requests](https://github.com/experimental-design/bofire/blob/main/CONTRIBUTING.md#pull-requests)?

Y

### Have you updated `CHANGELOG.md`?

No

## Test Plan

Unit tests.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9379322ce07c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
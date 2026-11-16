# Issue

**Title:** llm_hub: attribute requests to the Galaxy user

## Description

Fixes the first half of #1921.

## Problem

A Galaxy instance authenticates to its LiteLLM proxy with a **single shared key**, so every request looks identical to the proxy. Today `llm_hub.py` builds:

```python
api_params = {"model": model, "messages": messages, "stream": True}
```

— no `user` field, and the wrapper never passes the Galaxy user id. Consequently:

- usage/spend is trackable only in aggregate, not per user;
- LiteLLM's [end-user budgets](https://docs.litellm.ai/docs/proxy/users) (`/customer/new`, `max_end_user_budget_id`) can't be used at all — they key off the OpenAI `user` field;
- a shared instance-wide rate limit can be exhausted by one user, for everyone.

## Change

Pass `$__user_id__` from the wrapper and forward it as the standard OpenAI `user` field when set.

```diff
  '$model.fields.provider'
+ '$__user_id__'
```
```diff
  api_params = {"model": model, "messages": messages, "stream": True}
+ if galaxy_user_id:
+     api_params["user"] = galaxy_user_id
```

Two deliberate details:

- **`$__user_id__`, not `$__user_email__`.** This value is forwarded to the upstream provider, so the opaque numeric id keeps personal data out of it. Admins who want a different identifier can map it proxy-side.
- **Anonymous sessions.** Cheetah renders the id as the literal string `"None"`, which is normalised to empty, so `user` is simply omitted. Requests are byte-for-byte unchanged for anyone not doing per-user metering.

`VERSION_SUFFIX` bumped to 3.

## Testing

Running as an out-of-tree patch on [stage-usegalaxy.ch](https://stage-usegalaxy.ch) against a self-hosted LiteLLM proxy in front of the [CSCS](https://docs.cscs.ch/services/inference/) inference service. With `user` present, LiteLLM auto-creates the end-user record on first call and `max_end_user_budget_id` then applies a default TPM/RPM budget — which is what makes per-user fair-use possible at all.

`py_compile` and XML parse both clean. No test-data changes: the field only affects the outbound request, and the existing tests don't exercise a proxy that reports attribution. Happy to add coverage or adjust the identifier choice if you'd prefer something else.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `06994a0e3c5b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
# Issue

**Title:** Hello gxy-tool-bot

## Description

@bgruening please see bot config. assumes GXY_TOOL_BOT_API_KEY is set already and holds the cz token. also, we need labels before this will work, i can add them and comment back here once they exist. 

i set it to deepseek-thinking w qwen fallback for now. can change it to try different things as needed. but thats what ive been doing the last 24 hrs or so in my iuc fork though and so far at least while its slower it times out less and never fails entirely for that. glm use looks ok today, but was really heavy yest so i tried something else. honestly i think if we get the harness good enough (eventually lol) the model will matter less

other things to note.. can change timeout times, temperature, how many iterations to let it go before it has to make a commit etc in the bot config yml also. and if you want to restrict to specific maintainers, can do that in the yml to w:
```
allowed_maintainers:
  - your-github-handle
```

if any of those buttons and knobs youd rather not be in the bot config yml where others can see and pr against etc, let me know. i figured favor transparency s much as possible until i was given a reason to not.

its likely as i keep fiddling w things the workflows might get modified or cleaned up some, but i think where it is now is ok enough to try to get broader feedback on and see .

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3b717f66b612`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
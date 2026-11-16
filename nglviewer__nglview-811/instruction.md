# Issue

**Title:** ADD experimental code: "wait" to wait for data available

## Description

Without wait, below code does not work since the `value` of the widget is not updated but the subsequent codes are already executed.

## Without `wait`
<img width="433" alt="Screen Shot 2019-05-23 at 10 08 13 PM" src="https://user-images.githubusercontent.com/4451957/58297991-d484e380-7da7-11e9-8d75-0834281129d9.png">

## With `wait`
<img width="408" alt="Screen Shot 2019-05-23 at 10 07 41 PM" src="https://user-images.githubusercontent.com/4451957/58298011-e8c8e080-7da7-11e9-9b1a-247733fbea19.png">

PS: treat the code as sandbox.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6ff217bf67ff`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
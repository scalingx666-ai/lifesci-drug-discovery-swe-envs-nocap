# Issue

**Title:** Render image enhancement: we don't need `_display_image` anymore.

## Description

wow, finally I can make this work. 

In our current code (before this change), user needs to execute codes in two cells to make the display work
```
# cell 1
view.render_image()

# cell 2
view._display_image()
```

This change remove the drawback. Here is an example:
<img width="1012" alt="Screen Shot 2019-05-21 at 12 44 36 AM" src="https://user-images.githubusercontent.com/4451957/58068981-a1e9a980-7b61-11e9-9d87-d31bdf77822f.png">

Or even better, we can execute multiple `render_image` calls in a single cell, with the help from `time.sleep` and `threading`.

<img width="388" alt="Screen Shot 2019-05-21 at 12 38 13 AM" src="https://user-images.githubusercontent.com/4451957/58069013-c0e83b80-7b61-11e9-91f1-efd02c4e69a4.png">

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `bf9a1d817c61`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
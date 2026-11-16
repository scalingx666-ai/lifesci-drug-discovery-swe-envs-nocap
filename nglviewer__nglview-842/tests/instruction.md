# Issue

**Title:** Movie making without setting timeout

## Description

Final version
```python
from nglview.contrib.movie import MovieMaker

m = MovieMaker(view, in_memory=True, output='test.gif')
m.make()
```

![movie_making](https://user-images.githubusercontent.com/4451957/62596536-aeec7e00-b8b0-11e9-9171-39749892c964.gif)

This is useful for rendering/making movie a system with surface representation.
e.g:

![download](https://user-images.githubusercontent.com/4451957/62658369-a63e8b00-b936-11e9-9c74-dda37e528977.gif)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `23514df8fa34`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
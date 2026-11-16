# Issue

**Title:** Add BuildingBlock.get_num_placers()

## Description

Related Issues: #376

Requested Reviewers: @andrewtarzia

A new method, `BuildingBlock.get_num_placers()` has been added. This
is necessary because sometimes the number of placer atoms is necessary,
for example, by unaligning vertices, which needs to check the number of
placer atoms, in order to determine if the unaligning vertex should be
used. Previously all the placer ids would have to be iterated though
with `BuildingBlock.get_placer_ids()`, which is both ugly and less
performant.

<!--
Talk about what a user would see (a big, a new feature) and what
user goals weren't being met. If the commit fixes a bug, describe how
the bug was discovered and steps to reproduce it, unless this is
already covered by the related issues. If this is a bug fix, what was
the mistake in the application logic? Be precise. Act like a detective
and report your findings.
-->

<!--
Why did you make the change this way? What other ways did you consider
but reject? Explain how amazing your work is.
-->

<!--
What risks are associated with making the changes in the commit? Will
anything else break? Are the changes backwards-compatible? Is there
any "tech debt"?
-->

<!--
Explain the source code changes. Changes that are fully explained in
code comments or the above paragraphs don't need to be repeated here.
Use bullet points, e.g.

* `src/stk/molecular/atoms/atom.py:Atom.get_id()`: The method
  parameters were updated because <some reason>. The places where
  the method was called were also updated.
-->

<!--
Give evidence that the commit works. Did you visually inspect any
changes to molecular structures yourself?
-->

<!--
The suggested PR outline is taken from
https://joshuatauberer.medium.com/write-joyous-git-commit-messages-2f98891114c4
-->

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `851c09e2d74e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
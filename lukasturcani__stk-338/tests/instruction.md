# Issue

**Title:** Allow linear polymers from 1 building block

## Description

Related Issues: #288
Requested Reviewers: @andrewtarzia
*Note for Reviewers: If you accept the review request add a :+1: to this post*

@joshkamm feel free to have a look through / review this PR too
if you find the time. If you wanna comment (or not comment) after it's
been merged, that's OK too.

Users can now create a `Linear` polymer which has only 1 building
block. The implementation relies on adding a new vertex,
`_UnaligningVertex` which just places the building block. The idea
being that when there is only 1 building block, there is no need to
do any aligning.

In order to implement this change I factored out most of the old
initializer into a separate function, `_get_vertices_and_edges`. The
new initializer tries to unpack the list of orientations into a head,
body and  tail. If this succeeds, `_get_vertices_and_edges` will get
called. If it fails, it means that there is only 1 building block so
an `_UnaligningVertex` gets made instead.

The `_UnaligningVertex` has it's flipping always set to `False`. This
will  happen even if the probability of flipping is set to 1. This is
weird, but it simplifies the implementation and I do not think it
matters in practice. In any case, I have documented this behavior in
the docstring. If the flipping was allowed, it would mean that
`_UnaligingVertex` would actually have to start doing orientations, or
flips along some  axis, which I think is completely unnecessary.

The only way a user would notice this weirdness is if they print the
string representation of the topology graph. So one option could be
to let the representation show that the vertex does flipping, but
then not actually do it. I think this would also be weird, because if
the user checked if the position matrix had changed, it would not have,
and that's confusing too! So I think out of the options of doing
something completely unnecessary, versus having a string
representation that might not match the initialization parameters,
I think the latter is way better, because I really doubt anyone will
notice.

There is also the option of having representation that does not
show orientations for the case when the polymer is only made
from one building block. However, even in this case the user
might expect that by setting the orientations parameter to 0 or 1
different positions matrices will result. I could just prevent the
use of the orientation parameter for this case, but again I think
that's just too complicated overall.

There is also a minor change of moving the `polymer_linear_opt`
into just the `polymer_linear` test case. I don't see why a separate
fixture was made for `polymer_linear_opt`, I think it's just another
test case of `polymer_linear` that has no reason to be separated
from its friends.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b2814dda36b4`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
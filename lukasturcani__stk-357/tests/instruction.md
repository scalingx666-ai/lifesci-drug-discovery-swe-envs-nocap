# Issue

**Title:** Add setup for type hints

## Description

Requested Reviewers: @andrewtarzia  <!-- Add other reviewers here -->
*Note for Reviewers: If you accept the review request add a :+1: to this post*

This commit allows `stk` to use type hints. The purpose of type hints
is to give us the opportunity to use static type checking. In order
to use type hints, the types must be removed from docstrings, so that
they are not specified in two places, which would be a maintenance
burden. However, the types should still be present in the compiled
documentation. By using `sphinx_autodoc_typehints`, the types in
type hints are still present in the compiled docs. However, because
the NumPy style docstring require the return type of a function to
be present, a switch is going to be made to Google style docstrings,
which do not have this requirement.

This commit updates the docstrings of the `Atom` class as an initial
example of the changes going forward. The type hints will be
introduced gradually. Every commit which touches a a function must
introduce type hints to it and switch the docstrings to Google style.
Use of `mypy` in CI will not be introduced in this commit, but in a
later one, once more of code base has type annotations.

In order to implement type hints for the `Atom` class a couple of
things were changed. First, the default implementation was moved
from the `Atom` class itself, into `AtomImpl`. This is because the
`init_subclass` method was changing the `__init__` method of the
subclass, which was causing a type error. The code was safe, but I
think overall more confusing than just simply using inheritance to
override the init method. I also explicitly overrode the clone method
for all the elements, in order to support covariant return types.

This commit updates the `tests/docker/environment.yml` so that it
includes `sphinx_autodoc_typehints` as well as `mypy`.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0071184a43f9`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
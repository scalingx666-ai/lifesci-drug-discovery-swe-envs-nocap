# Issue

**Title:** Use unaligning vertex in Linear polymer

## Description

Related Issues: #156
Requested Reviewers: @lukasturcani
*Note for Reviewers: If you accept the review request add a :+1: to this post*

This PR makes no changes visible to the user but allows the user to place molecules like `BrCBr` on the `polymer.linear` topology graph using `UnaligningVertex`. This is handled by the Linear initializer when defining vertices (all vertices with building blocks that only have one placer are converted to a UnaligningVertex - same as in Cof and Cage).

* `src/stk/molecular/topology_graphs/polymer/linear/linear.py:_get_building_block_vertices`: Added a check for whether each vertex should be an UnaligningVertex.

* `src/stk/molecular/topology_graphs/polymer/linear/vertices.py:UnaligningVertex`: Added new init class method.

Two new tests added for vertex and molecule fixture.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `27951be4a13f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
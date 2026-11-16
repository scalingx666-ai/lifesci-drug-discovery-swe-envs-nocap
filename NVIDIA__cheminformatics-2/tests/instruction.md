# Issue

**Title:** CPU version for benchmarking and bugfixes...

## Description

Changes to switch between CPU and GPU. This change is only limited to dash (not yet implemented in notebook).

    Switching between CPU and GPU can be done from line 101 in startdash.py.


Bugfix: New MoI does not always add it to dataset and recluster

    Root cause for this was complex event hierarchy. Following were the events in
    question:
     - Onblur event from MoI input and click event from 'Highlight' button does the
       same thing(Re-cluster dataset and highlight MoI molecules).
     - Onblur event of MoI input was also used to manage 'Add to MoI' in the
       Molecular structure table.

    To fix this issue, onblur event is removed from MoI input. Now, the only way to
    recluster and highlight is by clicking 'Highlight' button. 'Add to MoI' is
    handled thru an onChange event emmitted from an hidden input element. This
    eliminates the race condition between onblur from MoI input and onclick from
    Highlight button.

    Another change in this PR, adds clusters with MoI to the top of the figure.


Bugfix: Adding MoI not in the origitnal dataset...

    On entering a new MoI the selection of the molecule was performed onblur event
    and reclustering was happeing on hitting 'Highlight' button. Due to these
    different event trying to complete this one task, the molecule does did not
    get highlighted.

    With this change both these event can perform this task such that reclustering
    is always performed before highlighting the molecule.

    This bug was hiding few other issues in the application.
     - Copying kmeans label was merging based on index. Since, index changes
       between every recluster event, new MoI got aligned with incorrect cluster

    Other changes include issues with reload. Post reload similar, issues were
    causing inconsistent behavior around clustering and highlighting molecule.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `66ef60b381bd`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
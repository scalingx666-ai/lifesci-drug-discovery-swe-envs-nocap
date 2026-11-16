# Issue

**Title:** added range_loagAUC as an evaluator

## Description

Author: Yunchao "Lance" Liu (lanceknight26@gmail.com)
Calculate logAUC in a certain FPR range (default range: [0.001, 0.1]).
This was used by previous methods [1] and the reason is that only a
small percentage of samples can be selected for experimental tests in
consideration of cost. This means only molecules with very high
predicted activity values can be worth testing, i.e., the decision
threshold is high. And the high decision threshold corresponds to the
left side of the ROC curve, i.e., those FPRs with small values. Also,
because the threshold cannot be predetermined, the area under the curve
is used to consolidate all possible thresholds within a certain FPR
range. Finally, the logarithm is used to bias smaller FPRs. The higher
the logAUC[0.001, 0.1], the better the performance.

A perfect classifer gets a logAUC[0.001, 0.1] ) of 1, while a random
classifer gets a logAUC[0.001, 0.1] ) of around 0.0215 (See [2])

References:
[1] Mysinger, M.M. and B.K. Shoichet, Rapid Context-Dependent Ligand
Desolvation in Molecular Docking. Journal of Chemical Information and
Modeling, 2010. 50(9): p. 1561-1573.
[2] Mendenhall, J. and J. Meiler, Improving quantitative
structure–activity relationship models using Artificial Neural Networks
trained with dropout. Journal of computer-aided molecular design,
2016. 30(2): p. 177-189.
:param true_y: numpy array of the ground truth. Values are either 0 (
inactive) or 1(active).
:param predicted_score: numpy array of the predicted score (The
score does not have to be between 0 and 1)
:param FPR_range: the range for calculating the logAUC formated in
(x, y) with x being the lower bound and y being the upper bound
:return: a numpy array of logAUC of size [1,1]

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `77eb9595d1ab`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
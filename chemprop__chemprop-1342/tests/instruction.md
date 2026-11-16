# Issue

**Title:** Use raw strings for math docs

## Description

## Description
When I run chemprop I get these messages:
```
mypath.venv/lib/python3.13/site-packages/chemprop/data/collate.py:15: SyntaxWarning: invalid escape sequence '\s'
  """A :class:`BatchMolGraph` represents a batch of individual :class:`MolGraph`\s.
mypath.venv/lib/python3.13/site-packages/chemprop/data/collate.py:22: SyntaxWarning: invalid escape sequence '\s'
  """A list of individual :class:`MolGraph`\s to be batched together"""
mypath.venv/lib/python3.13/site-packages/chemprop/data/collate.py:65: SyntaxWarning: invalid escape sequence '\s'
  """the number of individual :class:`MolGraph`\s in this batch"""
mypath.venv/lib/python3.13/site-packages/chemprop/data/datasets.py:190: SyntaxWarning: invalid escape sequence '\s'
  """A :class:`MoleculeDataset` composed of :class:`MoleculeDatapoint`\s
mypath.venv/lib/python3.13/site-packages/chemprop/data/datasets.py:362: SyntaxWarning: invalid escape sequence '\s'
  """A :class:`CuikmolmakerDataset` composed of :class:`LazyMoleculeDatapoint`\s and a
mypath.venv/lib/python3.13/site-packages/chemprop/data/datasets.py:636: SyntaxWarning: invalid escape sequence '\s'
  """A :class:`ReactionDataset` composed of :class:`ReactionDatapoint`\s
mypath.venv/lib/python3.13/site-packages/chemprop/data/datasets.py:697: SyntaxWarning: invalid escape sequence '\s'
  :class:`MoleculeDatasets` and :class:`ReactionDataset`\s"""
mypath.venv/lib/python3.13/site-packages/chemprop/featurizers/atom.py:132: SyntaxWarning: invalid escape sequence '\m'
  Include a bit for all atomic numbers in the interval :math:`[1, \mathtt{max\_atomic\_num}]`
mypath.venv/lib/python3.13/site-packages/chemprop/featurizers/molgraph/cache.py:14: SyntaxWarning: invalid escape sequence '\s'
  :class:`~chemprop.data.molgraph.MolGraph`\s.
mypath.venv/lib/python3.13/site-packages/chemprop/featurizers/molgraph/cache.py:48: SyntaxWarning: invalid escape sequence '\s'
  :class:`~chemprop.data.molgraph.MolGraph`\s and caches them in memory.
mypath.venv/lib/python3.13/site-packages/chemprop/featurizers/molgraph/cache.py:70: SyntaxWarning: invalid escape sequence '\s'
  :class:`~chemprop.data.molgraph.MolGraph`\s as they are requested.
mypath.venv/lib/python3.13/site-packages/chemprop/featurizers/molgraph/molecule.py:119: SyntaxWarning: invalid escape sequence '\s'
  """the number of individual :class:`MolGraph`\s in this batch"""
mypath.venv/lib/python3.13/site-packages/chemprop/data/dataloader.py:36: SyntaxWarning: invalid escape sequence '\s'
  """Return a :obj:`~torch.utils.data.DataLoader` for :class:`MolGraphDataset`\s
mypath.venv/lib/python3.13/site-packages/chemprop/nn/message_passing/proto.py:22: SyntaxWarning: invalid escape sequence '\s'
  the batch of :class:`~chemprop.featurizers.molgraph.MolGraph`\s to encode
mypath.venv/lib/python3.13/site-packages/chemprop/nn/message_passing/proto.py:52: SyntaxWarning: invalid escape sequence '\s'
  the batch of :class:`~chemprop.featurizers.molgraph.MolGraph`\s to encode
mypath.venv/lib/python3.13/site-packages/chemprop/nn/predictors.py:101: SyntaxWarning: invalid escape sequence '\s'
  """A :class:`_FFNPredictorBase` is the base class for all :class:`Predictor`\s that use an
mypath.venv/lib/python3.13/site-packages/chemprop/uncertainty/calibrator.py:123: SyntaxWarning: invalid escape sequence '\i'
  The target qunatile, :math:`p \in [0, 1]`
mypath.venv/lib/python3.13/site-packages/chemprop/uncertainty/calibrator.py:537: SyntaxWarning: invalid escape sequence '\h'
  corresponds to the in-set :math:`\hat{\mathcal C}_\text{in}`, while the second corresponds to
mypath.venv/lib/python3.13/site-packages/chemprop/uncertainty/estimator.py:640: SyntaxWarning: invalid escape sequence '\s'
  S = \sum_{i=1}^K \alpha_i
mypath.venv/lib/python3.13/site-packages/chemprop/uncertainty/estimator.py:712: SyntaxWarning: invalid escape sequence '\s'
  S = \sum_{i=1}^K \alpha_i
mypath.venv/lib/python3.13/site-packages/chemprop/uncertainty/evaluator.py:254: SyntaxWarning: invalid escape sequence '\m'
  \mathrm{NLL} = -\log(\hat{y} \cdot y + (1 - \hat{y}) \cdot (1 - y))
mypath.venv/lib/python3.13/site-packages/chemprop/uncertainty/evaluator.py:326: SyntaxWarning: invalid escape sequence '\m'
```

## Relevant issues
If appropriate, please tag them here and include a quick summary

## Checklist
- [x] linted with flake8?
- [x] (if appropriate) unit tests added? (no-code changes)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e3c13f091ee1`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
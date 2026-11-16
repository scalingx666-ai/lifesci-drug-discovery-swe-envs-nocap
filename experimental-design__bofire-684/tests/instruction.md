# Issue

**Title:** 675 fim matrix rank etc (replacing other pull request)

## Description

<!--
Thank you for sending the PR! We appreciate you spending the time to make BoFire better.

Help us to understand your motivation by explaining why you decided to make this change.

You can learn more about contributing to BoFire here: https://github.com/experimental-desgin/bofire/blob/main/CONTRIBUTING.md
-->

## Motivation

Use case: you have an existing DoE or experiments, and would like to get a sense of how 'good' they are for a planned new design with e.g. the same domain.  

There are various ways to do this, but the cheapest/fastest is to take the rank of the fisher information matrix (XTX) associated to the design matrix (X) built from your existing experiments and the (larger) design you're aiming for.  I acknowledge there are more sensitive approaches and this yields at best an overly optimistic estimate, but this is the one our group at BASF aligned on as the most pragmatic (we can talk about Kappa/condition number for the curious). 

In adding this functionality, I also tackled the issues with naming and some duplicate code in  #677  . No breaking changes, just internal variables renamed. Also added comments. 

### Functionality description: 
the quick and dirty way to say how many re-usable experiments are there would be to make the design matrix for the desired extended design, transform your experiments into that space and take the rank of that matrix.

Formulaic can handle this for continuous variables.
It can not handle it for categorical and discrete due to how we dummy-encode them. Thanks to  and  , we have the matrix we need already exposed, and then need to apply torch.rank (or whatever the appropriate rank function is).

I'll additionally altered logic around the get_number_of_experiments to have an optional handling of candidates/data that would then use this. That is in DoEStrategy, get_additional_experiments_needed  (no breaking change, just a new function). 
Open to re-naming. 

### Walkthrough 

#### ModelBasedObjective 

recall: from #631 now has a matrix function https://github.com/experimental-design/bofire/blob/db23c00914c9c545f3f065457ac3e5271ece285a/bofire/strategies/doe/objective.py#L103

(Added a test for that in test_objective. )

#### DoE Strategy

Added function to get candidate rank https://github.com/experimental-design/bofire/blob/db23c00914c9c545f3f065457ac3e5271ece285a/bofire/strategies/doe/objective.py#L109
It calculates the rank of the candidates in the relevant model matrix, using the function from ModelBasedObjective to get the model matrix tensor. 


**CORE FUNCTIONALITY: get_additional_experiments_needed**

Basically: experiments for the design + domain minus the goodness of the candidates. Mildly confusing, because the required number of experiments is often (min needed) + 3. 
 
https://github.com/experimental-design/bofire/blob/db23c00914c9c545f3f065457ac3e5271ece285a/bofire/strategies/doe_strategy.py#L240-253


####  utils_categorical_discrete 

Fair to warn others: 
The _transform_candidates_to_new_domain method sets missing (aux) columns to None, which creates NaN values. This happens at line 279:

https://github.com/experimental-design/bofire/blob/a5c092735a8ad4176c8f7a8cd3ebedcd5b9e6f3a/bofire/strategies/doe_strategy.py#L273-L279

Created a function that actually transforms things. 

https://github.com/experimental-design/bofire/blob/4a2758f97ae84263e004f07f82e8122d296a4240/bofire/strategies/doe/utils_categorical_discrete.py#L420-L425


### Have you read the [Contributing Guidelines on pull requests](https://github.com/experimental-design/bofire/blob/main/CONTRIBUTING.md#pull-requests)?

Yes

## Test Plan

in /tests/bofire/strategies/test_doe.py

- def test_get_candidate_rank():
- def test_get_candidate_rank_categorical_discrete():
- def test_get_additional_experiments_needed()

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6a4d3175c015`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
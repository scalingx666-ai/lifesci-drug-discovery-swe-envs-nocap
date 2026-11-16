# Issue

**Title:** Constructor Metadata (Lightweight)

## Description

Implements #648

Two choices had to be made (these arise equally for the other implementation proposal in #680):
- We store also the values of optional arguments that have not been passed explicitly. This is to make the result of non-default constructors consistent with what I can infer for `__init__`
- We are not storing permanent attributes even if they are part of the used constructor signature and retrieve them from the class instead. This means the converted values will be returned as part of `constructor_info` and NOT the original passed values. This is not optimal but the only reasonable alternative is to double store the items

Alternating a target via constructor info (use case of @dasmy):
```python
h = t.constructor_info

# Here you can change properties but its your responsibility
# to change / add only things that the respective constructor supports
# h['sigma'] = 5

# via convenience construtor
NumericalTarget.from_constructor_info(**h)

# or
c = h.pop("constructor")
if c == "__init__":
    t_new = NumericalTarget(**h)
else:
    t_new = getattr(NumericalTarget, c)(**h)
```

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c236c3871542`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
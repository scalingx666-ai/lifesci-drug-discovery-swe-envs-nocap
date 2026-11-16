# Issue

**Title:** Merge sample command with the example command

## Description

The PR merges removes `sample` as a standalone sub-command for ersilia, and instead merges it with `ersilia example`, wherein now the command is implemented as follows:

```bash
(ersilia) ~  ersilia example --help
Usage: ersilia example [OPTIONS] COMMAND [ARGS]...

  This command can sample both ersilia models, or inputs for a given or
  currently running model.

  For the model input, the number of examples can be specified, as well as a
  file name.

  Simple inputs only contain the essential information, while complete inputs
  contain key and other fields, potentially.

  For ersilia models, only model identifiers are returned for a given sample
  size.

Options:
  --help  Show this message and exit.

Commands:
  inputs
  models
```

Output from `ersilia example models --help`:

```bash
(ersilia)  ~  ersilia example models --help
Usage: ersilia example models [OPTIONS]

Options:
  -n, --n_samples INTEGER
  -f, --file_name TEXT
  --help                   Show this message and exit.
```

While output from `ersilia example inputs --help` is as below:

```bash
(ersilia)  ~  ersilia example inputs --help 
Usage: ersilia example inputs [OPTIONS] [MODEL]

Options:
  -n, --n_samples INTEGER
  -f, --file_name TEXT
  -s, --simple / -c, --complete
  -p, --predefined / -r, --random
  --help                          Show this message and exit.
```


The PR also removes the `InputSampler` class because it is redundant given that the ExampleGenerator class has the same functionality.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `632da2f61ed1`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
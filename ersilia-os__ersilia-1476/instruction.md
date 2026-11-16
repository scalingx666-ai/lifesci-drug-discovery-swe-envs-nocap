# Issue

**Title:** Make python api work

## Description

This PR aims to make the Python API, ie the `ErsiliaModel` class work as intended, ie through a synchronous API, without the keyword `async`. To that effect, the API now looks like:

```python
(ersilia) ☁  ~  python
Python 3.10.13 (main, Aug  1 2024, 16:45:21) [Clang 15.0.0 (clang-1500.3.9.4)] on darwin
Type "help", "copyright", "credits" or "license" for more information.
>>> from ersilia import ErsiliaModel
>>> em = ErsiliaModel("molecular-weight")
>>> em.fetch()
>>> em.serve()
>>> em.run("CCCCC")
<generator object ErsiliaModel._api_runner_iter at 0x131df52a0>
>>> res = list(em.run("CCCCC"))
>>> res
[{'input': {'key': 'OFBQJSOFQDEBGM-UHFFFAOYSA-N', 'input': 'CCCCC', 'text': 'CCCCC'}, 'output': {'value': 72.151}}]
>>>
```

A model can also be fetched outside of the `ErsiliaModel`, using the `ModelFetcher` class as follows:

```
(ersilia) ☁  ~  python
Python 3.10.13 (main, Aug  1 2024, 16:45:21) [Clang 15.0.0 (clang-1500.3.9.4)] on darwin
Type "help", "copyright", "credits" or "license" for more information.
>>> from ersilia.hub.fetch.fetch import ModelFetcher
>>> import asyncio
>>> mf = ModelFetcher()
11:11:55 | DEBUG    | Initialized with URL: None
11:11:55 | DEBUG    | Getting model source
11:11:55 | DEBUG    | Model getting fetched from DockerHub
>>> asyncio.run(mf.fetch('eos3b5e'))
11:12:02 | INFO     | Model doesn't exist on your system, fetching it now.
11:12:02 | DEBUG    | Starting fetching procedure
11:12:03 | DEBUG    | Decided to fetch from DockerHub
11:12:03 | DEBUG    | Fetching from DockerHub
11:12:03 | DEBUG    | Pulling model image from DockerHub
11:12:03 | DEBUG    | Image ersiliaos/eos3b5e:latest is not available locally
11:12:03 | DEBUG    | Docker image of the model is not available locally
11:12:04 | DEBUG    | The docker image ersiliaos/eos3b5e:latest exists in DockerHub
11:12:04 | DEBUG    | Pulling image ersiliaos/eos3b5e:latest from DockerHub...
11:12:04 | DEBUG    | Trying to pull image ersiliaos/eos3b5e
11:12:07 | INFO     | latest: Pulling from ersiliaos/eos3b5e
11:12:08 | INFO     | 1610a673316c: Pulling fs layer
11:12:08 | INFO     | a63944f9b22b: Pulling fs layer
11:12:08 | INFO     | a013c1d5ab7f: Pulling fs layer
11:12:08 | INFO     | f49977da0f96: Pulling fs layer
11:12:08 | INFO     | 4f4fb700ef54: Pulling fs layer
11:12:08 | INFO     | f0b9070bd1be: Pulling fs layer
11:12:08 | INFO     | 2245c7c08455: Pulling fs layer
11:12:08 | INFO     | 5681903e1eb3: Pulling fs layer
11:12:08 | INFO     | 5a10740c35b2: Pulling fs layer
11:12:08 | INFO     | 4f4fb700ef54: Pulling fs layer
11:12:09 | INFO     | a63944f9b22b: Download complete
11:12:09 | INFO     | 4f4fb700ef54: Download complete
11:12:09 | INFO     | 5681903e1eb3: Download complete
11:12:09 | INFO     | f0b9070bd1be: Download complete
11:12:09 | INFO     | a013c1d5ab7f: Download complete
11:12:10 | INFO     | 1610a673316c: Download complete
11:12:10 | INFO     | 2245c7c08455: Download complete
11:12:10 | INFO     | 5a10740c35b2: Download complete
11:12:10 | INFO     | f49977da0f96: Download complete
11:12:11 | INFO     | Digest: sha256:311c24955e6c98b8e89ae8614c8359e86d5487c74de90288a43dfa4d60196663
11:12:11 | INFO     | Status: Downloaded newer image for ersiliaos/eos3b5e:latest
11:12:11 | INFO     | docker.io/ersiliaos/eos3b5e:latest
11:12:11 | DEBUG    | Image pulled successfully!
11:12:11 | DEBUG    | Size of image 115.4606990814209 MB
11:12:11 | DEBUG    | Asynchronous and concurrent execution started!
11:12:11 | DEBUG    | Registering model eos3b5e in the file system
11:12:11 | DEBUG    | /Users/dhanshree/eos/dest/eos3b5e
11:12:11 | DEBUG    | /Users/dhanshree/eos/dest/eos3b5e/from_dockerhub.json
11:12:11 | DEBUG    | Writing service class pulled_docker /Users/dhanshree/eos/repository/eos3b5e/20241230111211/service_class.txt
11:12:11 | DEBUG    | Writing APIs
11:12:11 | DEBUG    | Using port 64208
11:12:11 | DEBUG    | Starting Docker Daemon service
11:12:11 | DEBUG    | Creating container tmp logs folder /Users/dhanshree/eos/sessions/session_94236/_logs/tmp and mounting as volume in container
11:12:11 | DEBUG    | Stopping all containers related to model eos3b5e
11:12:11 | DEBUG    | Trying to run container
11:12:12 | DEBUG    | Serving container eos3b5e_a2bd
11:12:12 | DEBUG    | Running container a2504f8b17ef9b342a5d2b328ac94fa04ea9364077ab9e0555b67b8c04bbc262
11:12:12 | DEBUG    | Container in http://0.0.0.0:64208 is not ready yet
11:12:13 | DEBUG    | Getting APIs
11:12:13 | DEBUG    | Getting them using info endpoint
11:12:13 | DEBUG    | Using URL: http://0.0.0.0:64208/info
11:12:13 | DEBUG    | Status code: 200
11:12:13 | DEBUG    | Writing file /Users/dhanshree/eos/repository/eos3b5e/20241230111211/apis_list.txt
11:12:13 | DEBUG    | ['run']
11:12:13 | DEBUG    | Stopping and removing container
11:12:13 | DEBUG    | Stopping all containers related to model eos3b5e
11:12:13 | DEBUG    | Stopping and removing container eos3b5e_a2bd
11:12:23 | DEBUG    | Container stopped
11:12:23 | DEBUG    | Container removed
11:12:23 | DEBUG    | Copying information file from model container
79ae44b3367aa02676faca5f35b00673c6fd589d6475d02d80bc1679fbee4592
6ec96422-851f-4247-847c-04dd3af6c9bf
11:12:23 | DEBUG    | Copying api_schema_file file from model container
0d80bd0129b585a039444c5b3635c9604ad47940b67b06d84884006ef2672c00
3ecbb976-5be8-4a31-8cd4-faddafe1e4eb
11:12:23 | DEBUG    | Copying status file from model container
0e20128678619139d74e313501ec7396f805aca41eb47aeaac02b5d340a6671c
ab19fe26-e22d-4038-98a7-eb037fa4ea3c
537e2d78fb00169ce0e0e846f75df4ca0e414bd003638138873ba1c3d5892b1a
40fdd692-d7eb-4794-84ad-f54bbefbd384
8b38606754abe870f7dbdc048115f09c66f1e0b6bafaebb02c8e6d4ba08c39a6
f511bb15-dd7d-43d8-b97c-389bf2babf20
cf4ee4cf7836f37135394032994271222d6e54cd6cd9489e061f85e9701abec1
da8707c9-bf98-49d9-ad10-5d36e8939be6
7925e8962e7fa22da07657faef4265caf99c9e9c17a9f0dfce35a0b9e95c2624
9c2f770a-8a79-410b-b44d-d691222dc0fe
3ad5c50162246f10b02c4e313d0cfe36441124e3e9fd4fb878e93b91166a83f7
74d03c29-bb79-4134-8bb4-156eaafd7f3b
11:12:25 | DEBUG    | Running standard CSV example
11:12:25 | DEBUG    | /Users/dhanshree/eos/dest/eos3b5e/example_standard_input.csv
11:12:25 | DEBUG    | /Users/dhanshree/eos/dest/eos3b5e/example_standard_output.csv
11:12:26 | DEBUG    | Usage: ersilia [OPTIONS] COMMAND [ARGS]...

  🦠 Welcome to Ersilia! 💊

Options:
  --version      Show the version and exit.
  -v, --verbose  Show logging on terminal when running commands.
  -s, --silent   Do not echo any progress message.
  --help         Show this message and exit.

Commands:
  auth       Log in to ersilia to enter contributor mode.
  catalog    List a catalog of models
  close      Close model
  delete     Delete model from local computer
  example    Generate input examples for the model of interest
  fetch      Fetch model from Ersilia Model Hub
  info       Get model information
  run        Run a served model
  serve      Serve model
  test       Test a model
  uninstall  Uninstall ersilia

11:12:26 | DEBUG    | No need to use Conda!
🚀 Serving model eos3b5e: molecular-weight

   URL: http://0.0.0.0:64218
   PID: -1
   SRV: pulled_docker
   Output source: local-only

👉 To run model:
   - run

💁 Information:
   - info
⛔ Model eos3b5e closed
11:12:42 | DEBUG    | File /Users/dhanshree/eos/dest/eos3b5e/example_standard_output.csv created successfully!
11:12:42 | DEBUG    | Removing log file: /Users/dhanshree/eos/dest/eos3b5e/standard_run.log
11:12:42 | DEBUG    | Writing model source to file
FetchResult(fetch_success=True, reason='Model fetched successfully')
>>> from ersilia import ErsiliaModel
>>> em = ErsiliaModel('eos3b5e')
>>> em.serve()
>>> res = list(em.run("CCCCC"))
>>> res
[{'input': {'key': 'OFBQJSOFQDEBGM-UHFFFAOYSA-N', 'input': 'CCCCC', 'text': 'CCCCC'}, 'output': {'value': 72.151}}]
>>>
```

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `99a0c310fa82`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.
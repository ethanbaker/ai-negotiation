# Human vs AI Negotiation

## Initialization

This project works with version 3.10.12 of Python in Linux/Unix based
environments and Google Colab. The ideal environment to run this project
is **Google Colab**, as this allows for easily-implemented graphing
capabilities. There is a section below the Google Colab usage that
entails how to run the project through the command line. However, this
is unfit for the current implementation and requires significant changes.

*In order to simulate AI agents in any capacity, you must first paste your
OpenAI key at the top of the notebook/file. If you do not paste a key,
you can only run human vs human negotiations.*

## Google Colab Usage

To run the project on Google Colab, simply upload the file into Google
Drive. From here, you can paste your OpenAI key and start running blocks.

### Installing Requirements

The first block in the notebook checks to make sure the `_ctypes` module
can be found. There is an error when installing `negmas` on newer
versions of Python where the `_ctypes` library is outdated, meaning
`negmas` cannot be installed. You do not have to rerun this block every time
you open the notebook and instead can use it as a debugging tool if
your packages do not install correctly.

You can install the necessary requirements by running the block with the
pip imports. This will bring up a warning about needing to restart the session
in order to fix packages that were previously imported in the runtime. You need
to click `Restart Session` button for this message to disappear and for the Google
Colab runtime to synchronize the imported packages. Once the session is
restarted, you can click on the pip import block, the OpenAI key declaration
block, and more blocks further down the project.

### Running a Simulation

Each block contains a comment above it that explains what the code below does.
Most of these blocks are static and do not need to be rerun during a session.
This includes prompts, AI tool calls, and the human and AI negotiator classes.

In order to run a simulation, edit the `agent_types` list and `starter_role`
variables at the top of the *Running the Negotiation* block. This will start
a simulation with the provided agent types where the given starter role
proposes the first outcome in the negotiation. For example, the configuration
below creates a human vs AI negotiation environment where the seller goes
first. The human would be the seller as they are listed first in the list of
agents.

```python3
agent_types = ["human", "ai"]
starter_role = "seller"
```

You can change any of the different parameters to create any negotiation
environment as you see fit. The `agent_types` array can be any combination of
`ai` or `human`, whereas the `starter_role` variable can either be `buyer` or
`seller`.

If you rerun any simulation, you **need** to rerun the *Negotiation Setup*
block.


## Command Line Usage (DEPRECATED)

If you are running this project through the command line you need to
have `pip` installed. `pip` is the package manager for python. To
upgrade pip, run the following command:

```bash
$ pip install -U pip
```

Next, you need to download the provided google notebook as a Python
file. Once you have the downloaded file (that will end with a `.py`),
you need to comment out the *Google Colab Testing* section and uncomment
out the *Command Line Section*. This ensures that the code can be
run through the command line.

### Creating a Virtual Python Environment

The first step for the program is to create a virtual environment for
Python inside the project workspace. This should create a `.venv`
directory.

You can create a virtual environment by using the following command:

```bash
$ python3 -m venv .venv
$ . .venv/bin/activate
```

You can check if the virtual environment was initialized correctly by 
running `which python`. This command should output your current working
directory concatenated with `.venv/bin/python`. If this command does not
output this path, the virtual environment was not set up correctly.

### Installing Requirements

Most of these requirements stem from one common libraries: `negmas`. This 
is the Python library that is used to simulate negotiations and provide
associated metrics. `negmas` was made specifically to simulate agents
using mathematical reasoning (such as using an identity function to
describe utility). However, because `negmas` allows for custom agent
implementations, we can create a custom agent implementation that uses
either human reasoning by asking for human input or large language model
reasoning.

You can install `negmas` using the following command:

```bash
$ pip install negmas
```

The other library that is installed currently is `openai`. This is used
to implement ChatGPT functionality to the `AINegotiator` agent.

You can install `openai` as follows:

```bash
$ pip install openai
```

When installing these requirements, you should remove the Google Colab
import statements at the top of the file. These lines are:

```
!pip install negmas
!pip install openai
```

### Running a Simulation

You can run the project by running the `runner.py` script with python
and the two provided agents you want to test and the role that will
start the negotiation. For example, the command below starts the
negotiation simulation with an AI agent as the buyer and human agent
as the seller.

```bash
$ python runner.py ai human buyer
```

You can exchange any of the different parameters. The first two
command line parameters will be either `ai` or `human`, whereas the
third command line will either be `buyer` or `seller`.
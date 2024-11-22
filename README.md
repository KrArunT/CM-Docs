# CM-Docs
https://docs.mlcommons.org/inference/benchmarks/language/llama2-70b/

## CM Installation
* Make current directory as home direcory where CM folder will be generated
```sh
export HOME=$PWD
```

* Follow [this link](https://access.cknowledge.org/playground/?action=install) for installation

```sh
sudo apt update -y
sudo apt install -y python3 python3-pip python3-venv git git-lfs wget curl
```

```sh
python3 -m venv cm
source cm/bin/activate

python3 -m pip install cmind -U

export CM_REPOS="$HOME/CM"

cm init --repo=mlcommons@cm4mlops --branch=mlperf-inference

git clone https://github.com/mlcommons/ck
export CM_HOME="$PWD/ck/cm/cmind"
cm reindex repo

cm test core
```

### Set up CM virtual environment

<details>
<summary><b>Click if you want to use Python virtual environment</b></summary>

We suggest you to install a python virtual environment via CM though it's not strictly necessary 
(CM can automatically detect and reuse your Python installation and environments):
```bash
cm run script "install python-venv" --name=loadgen
```

You can also install a specific version of Python on your system via:
```bash
cm run script "install python-venv" --name=loadgen --version=3.10.7
```

By default, CM will be asking users to select one from all detected and installed Python versions
including the above one, any time a script with python dependency is run. To avoid that, you 
can set up the following environment variable with the name of the current virtual environment:

```bash
export CM_SCRIPT_EXTRA_CMD="--adr.python.name=loadgen"
```

The `--adr` flag stands for "Add to all Dependencies Recursively" and will find all sub-dependencies on other CM scripts 

</details>


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

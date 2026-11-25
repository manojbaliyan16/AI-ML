# How to run the notebooks locally (macOS and Ubuntu)

Everything runs from the `.venv` in this repo (Python 3.13, packages listed in `requirements.txt`). No Colab needed. The commands are the same on macOS and Ubuntu except where marked.

Repo location on each machine (use `cd` to your own):

| Machine | Path |
|---|---|
| Mac | `/Users/manojkumar/Academy/AI-ML` |
| Ubuntu | `/home/t0230j7/AI-ML` |

## Run a notebook

```bash
cd <repo path>
source .venv/bin/activate
jupyter lab
```

JupyterLab opens in the browser. Open any notebook from the file tree, for example `Module_1_NP_PD/notebooks/session 4.ipynb`. Use the kernel named `Python 3` (or `AI-ML (.venv)`). Stop the server with Ctrl+C in the terminal.

Without activating the venv:

```bash
<repo path>/.venv/bin/jupyter lab
```

### Ubuntu: no browser opens

On a server, over SSH, or in a minimal desktop, the browser may not open by itself. Start it without a browser and open the printed URL (the one with `?token=...`) yourself:

```bash
jupyter lab --no-browser
```

To reach it from another machine over SSH, forward the port from that machine, then open `http://localhost:8888/lab?token=...` there:

```bash
ssh -L 8888:localhost:8888 <user>@<ubuntu-host>
```

### VS Code

Open the folder, open a `.ipynb`, click "Select Kernel", and pick `.venv` (or `AI-ML (.venv)`).

## First-time setup on a new machine

### Ubuntu prerequisites

```bash
sudo apt update
sudo apt install -y git wget unzip curl
curl -LsSf https://astral.sh/uv/install.sh | sh   # installs uv, then open a new terminal
```

`uv` downloads Python 3.13 itself, so you do not need `python3-venv` or a system Python 3.13.

### macOS prerequisites

`uv`, `wget` and `unzip` come from Homebrew or are already present: `brew install uv wget` (`unzip` is built in).

### Create the venv and kernel (both systems)

```bash
git clone https://github.com/manojbaliyan16/AI-ML.git
cd AI-ML
uv venv .venv --python 3.13
uv pip install --python .venv/bin/python -r requirements.txt
.venv/bin/python -m ipykernel install --user --name ai-ml --display-name "AI-ML (.venv)"
```

The `.venv` and the kernel are per machine. Neither is stored in git, so repeat this on each PC. To rebuild a broken venv, run `rm -rf .venv` first.

## Keeping two machines in sync

```bash
git pull        # before you start working
git add -A && git commit -m "..." && git push   # when you finish
```

Notebooks store their outputs, so editing the same notebook on both machines without pulling first causes merge conflicts. Pull before you start, push when you finish.

## Colab differences to know

- `!wget`, `!unzip` and `!mv` work as they are (`wget` and `unzip` must be installed: see the prerequisites above).
- The notebooks download the Zomato dataset into the notebook's own folder, because Jupyter runs a notebook with its folder as the working directory. The files land in `Module_1_NP_PD/`.
- The dataset is about 460 MB. It is ignored by git (`.gitignore`), so it will not be pushed. Each machine downloads its own copy the first time.
- The download cells are safe to re-run: `!wget -nc` skips an existing file, and `!unzip -o` overwrites without the "replace? [y/n]" prompt that would otherwise hang the cell forever.
- The Colab-only path `/content/zomato_dataset.csv` was changed to the relative `zomato_dataset.csv`. Use relative paths in new notebooks too, never `/content/...` or an absolute path, so they work on both machines.
- `Session_5.ipynb` cell 72 downloads the assignment data with `gdown`. The file `assignment_dataset.csv` has about 1 million rows.
- The first load of a dataset can take a minute or more. That is normal.
- `google.colab` imports and Drive mounting do not work locally. Replace them with a plain file path.
- `Session_5.ipynb` cell 11 raises `ValueError: could not convert string to float: 'NEW'`. That is an intentional teaching error in the notebook, not a setup problem.

## Verified

On macOS, all three Module_1 notebooks and both `pandas_eda` notebooks were run top to bottom with `jupyter nbconvert --execute` on the `.venv`. `Pandas Detailed Nov 26`, `session 4`, `Basic_1` and `01_titanic_questions` finish with no errors. `Session_5` finishes with only the cell 11 teaching error. The Ubuntu steps above were not run from the Mac, so confirm them on the Ubuntu PC.

## Add a package

```bash
source .venv/bin/activate
uv pip install <package>
```

Then add it to `requirements.txt`, and run `uv pip install --python .venv/bin/python -r requirements.txt` on the other machine after pulling.

## Troubleshooting

- `ModuleNotFoundError`: the notebook is on the wrong kernel. Switch the kernel to `Python 3` or `AI-ML (.venv)` and restart it.
- `AI-ML (.venv)` is missing from the kernel list: run the `ipykernel install` line above on this machine.
- `jupyter: command not found`: activate the venv first (`source .venv/bin/activate`).
- `wget: command not found` or `unzip: command not found`: install them (Ubuntu: `sudo apt install wget unzip`).
- A notebook seems stuck on `!wget`: the download server is slow. Wait, or check the zip size growing in the folder.
- Mac only: an old `~/edgeai` venv belongs to another project and is not used here.

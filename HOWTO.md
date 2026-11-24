# How to run the notebooks locally

Everything runs from the `.venv` in this repo (Python 3.13, JupyterLab, NumPy, pandas, matplotlib, seaborn, scipy, gdown). No Colab needed.

## Run a notebook

```bash
cd /Users/manojkumar/Academy/AI-ML
source .venv/bin/activate
jupyter lab
```

JupyterLab opens in the browser. Open any notebook from the file tree, for example `Module_1_NP_PD/session 4.ipynb`. Use the kernel named `Python 3` (or `AI-ML (.venv)`). Stop the server with Ctrl+C in the terminal.

Without activating the venv:

```bash
/Users/manojkumar/Academy/AI-ML/.venv/bin/jupyter lab
```

### VS Code

Open the folder, open a `.ipynb`, click "Select Kernel", and pick `.venv` (or `AI-ML (.venv)`).

## Colab differences to know

- `!wget`, `!unzip` and `!mv` work as they are (`wget` and `unzip` are installed on this Mac).
- The notebooks download the Zomato dataset into the folder you launch Jupyter from or the notebook's folder. Jupyter runs a notebook with its own folder as the working directory, so the files land in `Module_1_NP_PD/`.
- The dataset is about 460 MB. It is ignored by git (`.gitignore`), so it will not be pushed.
- The download cells were changed to be safe to re-run: `!wget -nc` skips an existing file, and `!unzip -o` overwrites without the "replace? [y/n]" prompt that would otherwise hang the cell forever.
- The Colab-only path `/content/zomato_dataset.csv` was changed to the relative `zomato_dataset.csv`. Use relative paths in new notebooks too, never `/content/...`.
- `Session_5.ipynb` cell 72 now actually downloads the assignment data with `gdown` (the line was commented out). The file `assignment_dataset.csv` has about 1 million rows.
- The first load of a dataset can take a minute or more. That is normal.
- `google.colab` imports and Drive mounting do not work locally. Replace them with a plain file path.
- `Session_5.ipynb` cell 11 raises `ValueError: could not convert string to float: 'NEW'`. That is an intentional teaching error in the notebook, not a setup problem.

## Verified

All three notebooks were run top to bottom with `jupyter nbconvert --execute` on the `.venv`. `Pandas Detailed Nov 26` and `session 4` finish with no errors. `Session_5` finishes with only the cell 11 teaching error.

## Set up again from scratch (new machine or broken venv)

```bash
cd /Users/manojkumar/Academy/AI-ML
rm -rf .venv
uv venv .venv --python 3.13
uv pip install --python .venv/bin/python -r requirements.txt
.venv/bin/python -m ipykernel install --user --name ai-ml --display-name "AI-ML (.venv)"
```

## Add a package

```bash
source .venv/bin/activate
uv pip install <package>
```

Then add it to `requirements.txt`.

## Troubleshooting

- `ModuleNotFoundError`: the notebook is on the wrong kernel. Switch the kernel to `Python 3` or `AI-ML (.venv)` and restart it.
- `jupyter: command not found`: activate the venv first (`source .venv/bin/activate`).
- A notebook seems stuck on `!wget`: the download server is slow. Wait, or check the zip size growing in the folder.
- Old `~/edgeai` venv: it belongs to another project and is not used here.

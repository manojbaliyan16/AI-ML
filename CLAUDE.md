# AI-ML learning repo

All work for this learner happens in this repo only. Remote: github.com/manojbaliyan16/AI-ML.

## Layout
- `Module_1_NP_PD/` course notebooks (reference material, do not edit)
- `python/`, `numpy/` topic folders (currently empty placeholders)
- `pandas_eda/` self-study track: Pandas and EDA, novice to advanced
  - `CHECKLIST.md` progress tracker (milestones 0-6), `ORIGINAL_PROMPT.md` the original request
  - `data/` small datasets, `notebooks/` learner work, `projects/` end-to-end projects
- New topics get their own top-level folder (`<topic>/data`, `notebooks`, `projects`), named so it cannot shadow an installed package (use `pandas_eda`, not `pandas`).

## Learner and tutor mode
- Learner knows basic Python and pandas and wants real competence, not nice-to-know detail.
- Give hints and name the right function. Do not write full solutions unless asked for the answer.
- To check work, read the saved `.ipynb` (outputs included). Remind the learner to save with Ctrl+S first.
- Ask for each answer as a plain-English comment under the cell.
- Never overwrite the learner's notebooks. Put new exercises or answer keys in new files.

## Environment
- Venv at `.venv` (Python 3.13), deps in `requirements.txt` (add new ones there). Kernel name: `ai-ml`, display "AI-ML (.venv)".
- Run: `source .venv/bin/activate && jupyter lab` from the repo root, or call `.venv/bin/python` directly. Use `uv pip install --python .venv/bin/python <pkg>` to add packages.
- Use relative data paths (`../data/...`), never `/content/...` or absolute paths.
- pandas is 3.x (string dtype, copy-on-write). Older tutorials may differ.
- `HOWTO.md` has Mac paths from another machine. Paths on this machine are under `/home/t0230j7/AI-ML`.

## Git
- `.gitignore` excludes `*.csv`, so only datasets whitelisted there are tracked (`pandas_eda/data/titanic.csv`). Large data must never be committed (GitHub limit 100 MB).
- Do not commit or push unless asked.

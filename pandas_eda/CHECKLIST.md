# Pandas and EDA checklist

Tick a box by changing `[ ]` to `[x]`. Do milestones in order.

## Setup
- [x] Python environment created (`.venv`, deps in `requirements.txt`)
- [ ] From the repo root run `source .venv/bin/activate && jupyter lab`, then open a notebook with the "AI-ML (.venv)" kernel (name `ai-ml`)
- [ ] Bookmark: pandas docs, Kaggle Learn, McKinney book

## Milestone 0: Python minimum
- [ ] Lists, dicts, loops, functions, f-strings
- [ ] List comprehensions
- [ ] Imports and using a library
- [ ] Drill: function that takes a list of numbers and returns a dict of summary stats

## Milestone 1: Pandas basics
- [ ] Series vs DataFrame
- [ ] `read_csv`, `head`, `info`, `describe`, `shape`, `dtypes`
- [ ] Selecting columns; `loc` vs `iloc`
- [ ] Boolean filtering (`&`, `|`, `isin`, `between`)
- [ ] `sort_values`, `value_counts`, `unique`, `nunique`
- [ ] Creating and renaming columns
- [ ] Kaggle Learn: Pandas course
- [ ] Drill: answer 20 plain-English questions about one CSV
- [ ] Done test: no more than a few syntax lookups

## Milestone 2: Data cleaning
- [ ] Missing data: `isna`, `fillna`, `dropna` and when to use each
- [ ] Duplicates
- [ ] `astype`, `to_datetime`, `to_numeric`
- [ ] `.str` methods
- [ ] `apply`, `map`, `np.where`
- [ ] Outliers (IQR method)
- [ ] `read_csv` options: `na_values`, `parse_dates`, `usecols`
- [ ] Kaggle Learn: Data Cleaning course
- [ ] Drill: clean dirty dataset 1 (write down every issue and fix)
- [ ] Drill: clean dirty dataset 2
- [ ] Drill: clean dirty dataset 3
- [ ] Done test: I always check nulls, dupes, dtypes before analysis

## Milestone 3: Aggregation and reshaping
- [ ] `groupby` with `agg` and named aggregation
- [ ] `transform`
- [ ] `merge` (inner, left, outer) and row-count checks
- [ ] `concat`
- [ ] `pivot_table`
- [ ] `melt`
- [ ] `rank`, `cumsum`, `shift`, `rolling`
- [ ] Drill: 10 questions answered with both `groupby` and `pivot_table`
- [ ] Drill: join two tables, predict row count before running
- [ ] 100 pandas puzzles (ajcr): first 50
- [ ] Done test: I can state the grain ("one row per what?") of any table

## Milestone 4: Visualization and EDA workflow
- [ ] matplotlib basics (figure, axes, labels)
- [ ] seaborn: histogram, box, scatter, bar, correlation heatmap, pairplot
- [ ] Picking a chart for the question
- [ ] Distributions, skew, correlation vs causation, Simpson's paradox
- [ ] Time series: `resample`, plot by date
- [ ] Memorize the 7-step EDA checklist
- [ ] Kaggle Learn: Data Visualization course
- [ ] EDA notebook 1 (with written conclusions)
- [ ] EDA notebook 2
- [ ] EDA notebook 3
- [ ] EDA notebook 4
- [ ] EDA notebook 5
- [ ] Kaggle Titanic EDA done
- [ ] Done test: a stranger can learn something true from my notebook

## Milestone 5: Intermediate fluency
- [ ] Method chaining: `assign`, `query`, `pipe`
- [ ] Vectorized ops instead of row-wise `apply`
- [ ] `.dt` accessor and time-based grouping
- [ ] Categorical dtype
- [ ] Performance: dtypes, `usecols`, `chunksize`
- [ ] Copy-on-write and `.copy()` in pandas 3
- [ ] Read/write Parquet, Excel, JSON, SQL
- [ ] Drill: rewrite earlier notebooks as chained pipelines
- [ ] Drill: time a slow `apply` against a vectorized version
- [ ] Done test: I can explain why a slow line is slow

## Milestone 6: Advanced and portfolio
- [ ] Confidence intervals and a t-test / chi-square
- [ ] Sampling bias
- [ ] `rolling`, `expanding`, `ewm`
- [ ] Cohort / retention table
- [ ] Funnel analysis
- [ ] Feature engineering: binning, encoding, lags
- [ ] Data validation with assertions
- [ ] SQL alongside pandas
- [ ] Project 1 with README (question, method, findings, limits)
- [ ] Project 2
- [ ] Project 3
- [ ] Done test: vague question + messy data -> trustworthy answer

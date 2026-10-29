**Process Theory**

**STAGE 1:**

1. Define the question: State the analytical goal *before* loading and cleaning data: what you want to know, for whom, and how you will measure success

2. Data loading: CSV (`read_csv`) · Excel (`read_excel`) · Kaggle Hub (`dataset_download` + `read_*`) · `concat` · `merge`

3. Missingness mechanisms = why a cell is empty, classified as MCAR, MAR, or MNAR.

* MCAR: Missing completely at random
* MAR: Missing depends on other observed columns
* MNAR: Missing depends on the hidden value itself

Fill missing values by column type

- Numeric, few missing, not the target → mean (use median if the distribution is skewed)
- Text / categorical → mode
- Missing target, invalid values (e.g. Age = −1), or too many missing rows → `dropna`, then `reset_index(drop=True)`
- Many “prefer not to say” cells (e.g. Cafe) → fill with `"Unknown"`

4. Data Wrangling: Discovery → Structuring → Cleaning → Enriching → Validating → Publishing

5. EDA = Description + visualization. Insights, not causation, not ML yet.

* 6-step EDA

1. Load — check `shape` and column meanings
2. Missing values and invalid entries
3. Outliers — IQR; drop vs clip / winsorize
4. Distributions — `describe`, histogram, countplot
5. Relationships — heatmap, box/violin; use rates over counts when group sizes differ
6. Feature engineering — datetime, new variables, binning, dummies, scaling
7. Summary — a few insights plus caveats

6. Visualization [your self-study] — Matplotlib for control; Seaborn for fast statistical plots from a DataFrame.

**Matplotlib** (`import matplotlib.pyplot as plt`)
Python’s standard 2D plotting library.

- Two APIs: Pyplot (`plt.plot`) vs object-oriented (`fig, ax = plt.subplots()`)
- Core plots: line, scatter, bar, histogram
- Layout: `subplots` for several axes on one figure
- Use when: you need titles, limits, layout, and export (`savefig`)

**Seaborn** (`import seaborn as sns`)
Statistical layer on top of Matplotlib — does not replace it.

- Data: DataFrame columns; color by group with `hue`
- Plots: scatter, line, bar, countplot, hist, box, violin, heatmap, pairplot
- Facets: `relplot` / `catplot` (`col`, `row`)
- Theme: `sns.set_theme()`
- Use when: fast EDA; still use `ax` / `plt` for polish and saving

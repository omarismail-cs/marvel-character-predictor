# Marvel alignment predictor

This project asks a simple question: **can we guess if a Marvel character is a hero type or a villain type from data we have about them?**

The main work lives in **`Marvel_Project.ipynb`**. Open that file in Jupyter or VS Code and run the cells from top to bottom.

## What is in this folder

| File | What it is |
|------|------------|
| `Marvel_Project.ipynb` | The full walkthrough: load data, clean it, build models, print accuracy. |
| `HeroesList.csv` | Starting table of many comic characters (not only Marvel), with names, alignment, looks, height, weight, and publisher. |
| `marvel_final_enriched.csv` | A Marvel-focused slice with short biography text added under `Wiki_Bio`, plus the same kind of table columns. |

There is also an auto-save copy of the notebook under `.ipynb_checkpoints`. You can ignore it.

## What the notebook does (in order)

1. **Loads and cleans** `HeroesList.csv`, drops unclear alignments, focuses on Marvel where the narrative steps need it.
2. **Baseline model** uses only height and weight. Accuracy is modest because body size does not match morality.
3. **Keyword model** reads each biography and counts how often a small list of “hero-ish” or “villain-ish” words shows up, then adds those counts plus height and weight. Accuracy goes up a lot.
4. **Full-text model** reads `marvel_final_enriched.csv` and uses **all** of each biography in a structured way (word patterns the library turns into numbers), plus gender, eye color, race, hair color, height, and weight. It tries a few settings automatically and usually scores **a few points higher** than the keyword-only approach on the characters set aside for testing.

Numbers like **62%**, **77%**, and **about 81%** appear in the notebook text and printouts. Your exact printed scores can shift slightly when the step that picks settings runs again.

## What you need installed

- Python 3 (the project was written using 3.12; nearby versions usually work).
- **pandas** and **scikit-learn** (and **scipy**, which scikit-learn relies on).

If something is missing, install it with pip, for example:

```bash
pip install pandas scikit-learn
```

## How to run

1. Clone or download this folder.
2. Open `Marvel_Project.ipynb`.
3. Run all cells. Stay in the same folder so the notebook can find the CSV files.

If you change the CSV files or how the notebook splits train versus test data, reported accuracy will change.

## Limits (good to know)

- Labels come from the dataset. Gray-area characters are forced into hero or villain buckets.
- Short or wrong biographies limit how well any model can do.
- Higher scores partly reflect **story wording**, not real-world ethics.

That is the whole picture in plain terms.

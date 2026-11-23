# Matching product names to an item master: four methods compared

Four ways to match hybrid names to a product item master (rules, n-grams, learned code cores, LightGBM), measured against known truth. Built with substantial AI assistance.

**Read it as a web page:** [https://joeybudi.github.io/projects/hybrid-name-matching/](https://joeybudi.github.io/projects/hybrid-name-matching/)

> **🤖 Built with substantial AI assistance.** An AI coding assistant was used heavily for this analysis: building the four matcher variants, running them side by side, tracing the cases where they disagreed, and drafting the comparison. I set the goal, decided what counts as a correct match, reviewed the disputed cases, and chose the method to adopt.

A ratings list scores seed hybrids by name, and each row has to be linked to every matching SKU in a product item master. This notebook builds four complete matchers, runs them on the same inputs, and measures each one's precision and recall.

## Key results

- Learned code core + trait gate: best as-is (F1 92%, precision 98.7%), with a reason recorded for every decision.
- N-gram matching has the highest recall but accepts hundreds of wrong trait versions.
- LightGBM trained on the rules method's output inherits its one-digit-sibling errors. Retrained on correct labels, it becomes the best method (F1 99%).

## What's in the notebook

- Rules + Levenshtein distance
- Character 3-gram containment + learned code core
- Learned code core with exact match and a hard trait gate
- LightGBM pair classifier and a label-quality counterfactual
- Error breakdown and a disagreement review queue

## About the data

All data in this repo is **simulated**. The original analysis ran on proprietary data, so this version keeps the methods and replaces the data and column names with realistic, generic stand-ins. The notebook generates its own data.

## Run it

```bash
python -m venv .venv
source .venv/bin/activate      # Windows: .venv\Scripts\activate
pip install -r requirements.txt
jupyter notebook hybrid_name_matching.ipynb
```

The notebook is saved with its outputs, so you can also just open it on GitHub.

## Author

Joey Budi · [joeybudi.github.io](https://joeybudi.github.io) · [LinkedIn](https://www.linkedin.com/in/jbudi)

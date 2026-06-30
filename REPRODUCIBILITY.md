Reproducibility instructions for MetaFlow experiments

This file contains the exact commands and configuration used to reproduce the
experiments reported in the paper. It assumes a Python 3.8+ environment on
Windows/Linux and a checked-out copy of the repository.

1) Create and activate a virtual environment (recommended)

Windows (PowerShell):
```
python -m venv .venv
.\.venv\Scripts\Activate.ps1
pip install --upgrade pip
```

Linux/macOS:
```
python3 -m venv .venv
source .venv/bin/activate
pip install --upgrade pip
```

2) Install dependencies

```
pip install -r requirements.txt
```

3) Example runs (produce JSON reports)

- Heart disease (small example):
```
python examples/sample_usage.py --dataset data/heart.csv --target target --output reports/heart_report.json --seed 42
```

- Credit card fraud (larger example):
```
python examples/rule_based_selection_demo.py --dataset data/creditcard.csv --target Class --output reports/creditcard_report.json --seed 42 --time_budget 3600
```

4) Producing a formal benchmark (MetaFlow + AutoML baseline)

- Run MetaFlow to produce a pruned candidate set and save the pipeline configs:
```
python -m src.main MetaFlowAgent.run --dataset data/your_dataset.csv --target target --save_candidates candidates.json --max_iterations 0
```

- Run Auto-sklearn on the reduced candidate set (example placeholder):
```
# adapt to your Auto-sklearn wrapper to accept a candidate list
python tools/run_autosklearn_on_candidates.py --candidates candidates.json --time_budget 1800 --output reports/autosklearn_on_pruned.json
```

- For baseline Auto-sklearn/FLAML runs, run them with the same dataset splits
and time budgets used above.

5) Recommended evaluation protocol

- Use nested CV for final reporting: outer 5 folds, inner 3 folds for tuning.
- Fix RNG seeds for reproducibility (e.g., `--seed 42`).
- Log the number of model evaluations and wall-clock time for each run.

6) Notes

- If a dataset file in `data/` is missing, download it from the URL in
`references.bib` or the dataset provider and place it under `data/` with the
expected filename.
- For large datasets, increase `--time_budget` and ensure sufficient RAM.

7) Outputs

- The example scripts write JSON files containing `metadata`, `all_pipelines`,
  `evaluation_report`, and per-pipeline logs. Use the `scripts/convert_reports.py`
  helper (if present) to build the LaTeX tables and figures used in the paper.

If you want, I can (A) add a PowerShell and Bash wrapper script to automate the
above steps, or (B) run the small examples now and attach the generated JSON
reports. Which do you prefer?
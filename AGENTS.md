# AGENTS.md — Project Assistant Guide

Purpose: Help AI coding agents immediately understand MetaFlow and assist with common tasks, including producing and improving the attached paper (`springer.tex`). Keep this file minimal and link to detailed docs.

## Quick Summary
- **Project:** MetaFlow — metadata-driven AutoML pipeline agent.
- **Language:** Python 3.8+
- **Entry point:** `src.main.MetaFlowAgent` (see [src/main.py](src/main.py#L1)).

## Key Locations
- **Architecture & components:** [docs/ARCHITECTURE.md](docs/ARCHITECTURE.md#L1)
- **API reference:** [docs/API.md](docs/API.md#L1)
- **Rule-based selection:** [docs/RULE_BASED_MODEL_SELECTION.md](docs/RULE_BASED_MODEL_SELECTION.md#L1)
- **Preprocessing details:** [docs/PREPROCESSING.md](docs/PREPROCESSING.md#L1)
- **Paper draft:** [springer.tex](springer.tex#L1)
- **Examples:** [examples/rule_based_selection_demo.py](examples/rule_based_selection_demo.py#L1), [examples/sample_usage.py](examples/sample_usage.py#L1)

## Useful Commands
- Install dependencies: `pip install -r requirements.txt`
- Run Streamlit UI: `streamlit run app.py`
- Run unit tests: `pytest -q`

## How an AI agent should help write the paper
1. Map each paper section to code and experiments:
   - Methods: link to `src/data/metadata.py`, `src/pipeline/model_selector.py`, `src/detection/task_detector.py`.
   - Experiments: reproduce examples in `examples/` and run `src.main.MetaFlowAgent.run()` on datasets in `data/`.
   - Results: programmatically collect metrics from `src/model/evaluator.py` outputs and generate tables/figures.
2. Extract reproducible commands and minimal scripts to (a) re-run experiments, (b) produce CSVs/plots for the paper.
3. Update `springer.tex` with precise numbers, figure file paths (e.g., `figs/roc_d2.png`), and a short methods appendix linking to `docs/`.
4. Propose small edits to improve clarity and match academic style (concise contributions, limitations, reproducibility notes).

## Priorities for paper-writing tasks
- Reproduce experiments that back claims in `springer.tex` (D1–D4 described in draft).
- Generate clear tables and small, publication-quality figures (ROC, confusion matrices, metadata heatmap).
- Add reproducibility checklist and commands in supplementary material.

## Development notes for agents
- Prefer linking to existing docs rather than copying large sections.
- When editing `springer.tex`, preserve LaTeX structure and only alter content that reflects reproduced results.
- If experiment reproduction is not possible (missing datasets or compute limits), produce an explicit "Reproducibility plan" listing required steps and scripts.

---
If you'd like, I can now: (A) run the example scripts and collect metrics, or (B) edit `springer.tex` with clearer exposition and checklist. Which should I do first?

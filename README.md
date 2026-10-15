# AI, Machine Learning & NLP Projects

A portfolio of five applied machine-learning and natural-language-processing projects spanning workforce analytics, educational content classification, memory-retention scheduling, generative math tutoring, and feedback analytics.

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](./LICENSE)

## Project index

| Project | Focus | Main techniques | Repository documentation |
|---|---|---|---|
| AttritionX | Employee attrition risk modeling | Logistic Regression, CatBoost, Keras neural network, feature selection and explainability | [Open project README](./AttritionX%3A%20Triangulated%20ML%20Pipeline%20for%20Employee%20Attrition%20Prediction/README.md) |
| Automated Content Tagging Pipeline | Subject classification for learning material | TF-IDF + Logistic Regression baseline; fine-tuned DistilBERT | [Open project README](./Automated%20Content%20Tagging%20Pipeline%20%E2%86%92%20NLP%20classification%20of%20learning%20material/README.md) |
| MARS — Memory and Retention Scheduling | Estimate forgetting rates and schedule reviews | Log-linear forgetting curves; a Keras regression experiment | [Open project README](./Mars/README.md) |
| MathGPT & TeacherGPT | Step-by-step math-solution generation and tutoring interface | FLAN-T5, PyTorch, beam-search generation, Gradio UI code | [Open project README](./mathGPT%26teacherGPT/README.md) |
| Sentiment Analysis & Churn-Rate Proxy | Classify NPS feedback and summarize feedback-based indicators | TF-IDF + Logistic Regression; DistilBERT; NPS-derived indicators | [Open project README](./sentiment%20analysis%20and%20churn%20rate%20prediction/README.md) |

## What the portfolio demonstrates

- Classical text classification and transformer-based NLP fine-tuning.
- Supervised learning workflows with train/validation/test splits and model-evaluation plots.
- Feature importance and feature-selection experiments, including SHAP, permutation importance, and variance-inflation-factor checks in AttritionX.
- A mathematical forgetting-curve baseline alongside a neural regression experiment in MARS.
- Encoder-decoder generation with a FLAN-T5 checkpoint workflow for step-by-step math responses.
- Dataset-bounded NPS calculations and sentiment labels derived from documented score thresholds.

## Repository layout

```text
ai-ml-nlp-projects/
├── AttritionX: Triangulated ML Pipeline for Employee Attrition Prediction/
├── Automated Content Tagging Pipeline → NLP classification of learning material/
├── Mars/
├── mathGPT&teacherGPT/
├── sentiment analysis and churn rate prediction/
├── README.md
└── LICENSE
```

Each project README describes its own inputs, techniques, assets, prerequisites, known limitations, and execution notes. Dependency versions are not standardized across the repository; use the requirements file provided for a particular model branch where one exists.

## Reproducibility and data availability

The repository contains a mix of datasets, CSV outputs, plots, and Python files exported from Google Colab notebooks. A `.py` file is not necessarily a directly executable command-line application: some source files include notebook-only `!pip` commands, `display()` calls, `/content/...` paths, assumptions about earlier notebook cells, or outputs/checkpoints that are not checked in.

Known input gaps in the current repository snapshot:

- **AttritionX:** model branches expect `/content/data_csv.csv`; the employee dataset is not included in the repository inventory.
- **MARS:** the baseline and Keras scripts expect `students.csv`, `topics.csv`, and `interactions.csv`. The project directory includes `interactions.csv` and a baseline `recommendations.csv`, but does not include `students.csv` or `topics.csv`. The Keras script also has unresolved dependencies on intermediate variables such as `recs` and `lambda_true`.
- **MathGPT & TeacherGPT:** the code expects `mathgpt_dataset.csv` and a saved `mathgpt_flan_t5_small` model/tokenizer directory; these inputs/artifacts are not present in the repository inventory. The Gradio launch call is commented out in the checked-in script.
- **Automated Content Tagging Pipeline:** the checked-in CSVs contain 50 templated topic rows. This is useful for demonstrating the workflow, but it is too small and synthetic to establish real-world generalization.
- **Sentiment Analysis & Churn-Rate Proxy:** the 100-row `nps_feedback.csv` is present. Labels are derived from NPS thresholds, and the churn figure is a detractor-rate proxy—not a validated prediction of future customer/student churn.

The included plots and output CSVs should be treated as evidence of documented runs, not as a guarantee that every current source file can reproduce them without data preparation or notebook-cell corrections.

## Suggested evaluation standard

When reviewing a model, inspect the data source and split strategy, compare validation and test metrics, verify whether labels are independently observed or rule-derived, and check whether model artifacts and preprocessing objects are included. Metrics from different model branches or historical runs should not be compared unless the dataset split and evaluation procedure are aligned.

## Author

**Shubham Kumar Singh**

## License

This project is licensed under the MIT License. The complete license is available in [`LICENSE`](./LICENSE) and reproduced below.

MIT License

Copyright (c) 2026 Shubham Kumar Singh

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.

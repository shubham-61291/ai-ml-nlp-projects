# Sentiment Analysis & Churn-Rate Proxy from NPS Feedback

This project classifies feedback into Negative, Neutral, or Positive labels based on Net Promoter Score (NPS) thresholds, compares a TF-IDF/Logistic Regression baseline with a fine-tuned DistilBERT classifier, and computes summary NPS and detractor-rate indicators.

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](./LICENSE)

## Data and label rules

The checked-in `nps_feedback.csv` has 100 records and these columns: `student_id`, `nps_score`, and `feedback_text`.

The source assigns a sentiment label from `nps_score`:

| NPS score | Assigned label |
|---|---|
| 0–6 | Negative |
| 7–8 | Neutral |
| 9–10 | Positive |

This means the model target is a rule-derived label from the numerical NPS score; it is not an independently human-annotated sentiment label in the checked-in data.

## Modeling workflow

- **Baseline classifier:** TF-IDF features and Logistic Regression, with train/validation/test split, classification report, and confusion matrix.
- **Transformer classifier:** `distilbert-base-uncased` fine-tuned with Hugging Face Transformers/Datasets and evaluated on a held-out test split. The source includes evaluation metrics and visual outputs.
- **NPS and proxy metrics:** NPS = promoter percentage (scores 9–10) minus detractor percentage (scores 0–6). The script defines the estimated churn/“iteration” rate as the detractor percentage and estimated retention as 100% minus that rate.

## Running in Google Colab

The script is a Colab notebook export, with a `!pip install` command and paths such as `/content/nps_feedback.csv`. It is not directly executable unchanged with an ordinary Python interpreter.

1. Open a new Google Colab notebook.
2. Upload `nps_feedback.csv` into the runtime or update the data path.
3. Install `pandas`, `numpy`, `torch`, `scikit-learn`, `seaborn`, `matplotlib`, `transformers`, `datasets`, `accelerate`, and `evaluate` as needed for the sections you run.
4. Run the baseline and transformer cells in order; the transformer downloads `distilbert-base-uncased` on first use.
5. Review the generated classification reports, confusion matrices, and loss plot.

## Interpretation and limitations

- The computed detractor fraction is an **NPS-derived proxy**, not a supervised model of observed future churn. The dataset does not include a separate outcome indicating whether a student or customer actually left.
- Because target labels are defined from NPS score thresholds, high classification accuracy only shows reproduction of that rule on the selected split; it does not validate independent sentiment understanding or future churn prediction.
- The dataset is small (100 rows), and test-set performance will be uncertain. Existing screenshots/results should not be interpreted as evidence of production generalization.
- The current source focuses on model training and analysis rather than a production service. It does not provide an independently validated churn intervention policy.
- NPS and retention definitions should be validated against the business's actual measurement practice before use in decisions.

## Included artifacts

- `nps_feedback.csv` — NPS feedback data.
- `sentiment_analysis_and_churn_rate_prediction.py` — combined notebook export.
- `basicmodel.png` — baseline confusion-matrix image.
- `distilledBERTmodel.png` — DistilBERT confusion-matrix image.
- `linegraph.png` — training/validation loss plot.

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

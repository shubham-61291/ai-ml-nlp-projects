# Automated Content Tagging Pipeline — NLP Classification of Learning Material

This project classifies learning-topic text by subject using a classical TF-IDF baseline and a fine-tuned DistilBERT sequence classifier. It also exports predicted subject labels for use by downstream learning workflows.

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](./LICENSE)

## Scope

The source data combines `title` and `description` into a text field and uses `subject` as the supervised target. The five subject labels represented in the checked-in data are Mathematics, Biology, Physics, History, and Chemistry, with 50 templated topic rows in total.

The script includes two approaches:

1. **Baseline:** `TfidfVectorizer` with Logistic Regression, followed by a classification report and confusion matrix.
2. **Transformer:** `distilbert-base-uncased` fine-tuned with a manual PyTorch loop for four epochs, using a stratified 80/10/10 train/validation/test split and reporting accuracy, macro-F1, a confusion matrix, and train/validation loss.

The script maps difficulty labels to an ordinal code during data preparation, but the trained classifiers described here target **subject classification**, not a separately trained difficulty-prediction model.

## Included data and outputs

| File | Purpose |
|---|---|
| `topics.csv` | Topic ID, title, and description; 50 rows |
| `topics_with_tags.csv` | Subject, difficulty, and tag labels aligned by `topic_id` |
| `topics_predicted_subjects.csv` | Checked-in subject predictions for the topic rows |
| `simplemethod.png` | Baseline confusion-matrix plot |
| `LINECHART.png` | DistilBERT train/validation loss plot |
| `DISTILBERT.png` | DistilBERT confusion-matrix plot |
| `automated_content_tagging_pipeline_→_nlp_classification_of_learning_material.py` | Combined training/evaluation notebook export |

## Run in Google Colab

The checked-in source was exported from a Colab notebook. It includes `!pip` installation commands, `/content/...` paths, and `display()` calls, so it is not a plain standalone Python script as committed.

1. Create a Colab notebook and upload or copy `topics.csv` and `topics_with_tags.csv` into `/content/`.
2. Install the dependencies used by the relevant cells: `pandas`, `scikit-learn`, `seaborn`, `matplotlib`, `torch`, `transformers`, `datasets`, and `accelerate`.
3. Run the baseline and transformer sections in order. The transformer section downloads the public `distilbert-base-uncased` model from Hugging Face and requires network access on first use.
4. The final export cell writes `topics_predicted_subjects.csv` to the active notebook working directory.

For local execution, remove the notebook-only `!pip` statements, replace `/content/` paths with normal paths, and provide an appropriate Python environment. That conversion is not part of the checked-in source.

## Evaluation and limitations

- The checked-in topic text is templated and highly separable by subject words. Very high or perfect metrics on this dataset are not evidence of production-grade subject classification.
- The test split is small (about five examples under the documented split), so metrics have high sampling uncertainty.
- The current pipeline does not implement a separately validated personalized difficulty model, adaptive learning policy, or learner-outcome evaluation.
- The predicted CSV is a saved output artifact; it is not proof that the full training pipeline has been rerun against the current environment.

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

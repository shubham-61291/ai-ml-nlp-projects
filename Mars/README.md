# MARS — Memory and Retention Scheduling

MARS explores how observed learning scores can be used to estimate a forgetting rate and recommend a future review date. It includes a mathematical baseline and a separate Keras regression experiment.

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](./LICENSE)

## Methods

### 1. Log-linear forgetting-curve baseline

The baseline groups interactions by student and topic, selects up to the earliest three observations, normalizes observed scores to a 0–1 range, and fits a log-linear model to estimate initial retention strength (`R0_hat`) and forgetting rate (`lambda_hat`). It then estimates the time at which retention reaches the configured 60% threshold and writes `recommendations.csv`.

### 2. Keras regression experiment

The Keras script describes a dense neural network that predicts a log-transformed forgetting-rate target from student features, topic difficulty, and one-hot subject features. The script specifies an 80/10/10 train/validation/test split, standard scaling, a 64/32-unit dense model, and 50 training epochs. It reports MAE, RMSE and R² for the forgetting-rate target and estimates review-day error.

These are two different implementation paths. The Keras path must not be assumed to be reproducible from the baseline output unless its data preparation and target construction are aligned.

## Files and current data availability

| File | Description |
|---|---|
| `mars_–_memory_and_retention_scheduling.py` | Mathematical baseline notebook export |
| `mars_–_memory_and_retention_scheduling_using_keras.py` | Neural regression notebook export |
| `interactions.csv` | Checked-in interaction-data asset |
| `recommendations.csv` | Checked-in baseline result artifact |
| `learning_loss_curve.png` | Keras training/validation loss plot |
| `dot_plot.png` | True-versus-predicted forgetting-rate plot |
| `error_distribution.png` | Review-day prediction-error plot |

**Required inputs missing from the repository:** both scripts read `students.csv` and `topics.csv`, but these files are not present in the current project directory listing. The Keras script also references intermediate names such as `recs` and `lambda_true` without constructing them inside that standalone file. As checked in, the neural script therefore needs notebook-state/data-preparation corrections before it can run independently.

## Running the baseline

The files are exported from Google Colab and use notebook features such as `display()`. For the intended notebook workflow:

1. Open the relevant source as cells in Colab.
2. Upload `students.csv`, `topics.csv`, and `interactions.csv` with the expected columns.
3. Run the baseline cells in order. The baseline expects student columns `student_id`, `grade`, `ability`, `diligence`; topic columns `topic_id`, `subject`, `difficulty`; and interaction columns `student_id`, `topic_id`, `learned_on`, `obs_date`, `days_since_learned`, and `score_observed`.
4. Inspect the fitted curves and generated `recommendations.csv`.

For the Keras branch, first repair the missing intermediate-state/data-target steps noted above and then rerun the entire pipeline. A plain `python ...py` command is not guaranteed to work on these notebook exports without adaptation.

## Limitations

- The 60% retention target is a configured modeling assumption, not a validated pedagogical threshold for every learner or topic.
- Forgetting-rate estimates depend on observation quality and the number/timing of recorded interactions.
- The committed output CSV and plots are artifacts; they do not establish that either current source file executes end to end with only the committed assets.
- Recommendations should be evaluated with prospective learner outcomes before being used to drive real academic interventions.

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

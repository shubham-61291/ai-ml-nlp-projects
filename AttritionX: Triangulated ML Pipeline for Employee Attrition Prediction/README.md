# AttritionX — Triangulated Employee Attrition Modeling

AttritionX groups three separate model experiments for employee-attrition classification: Logistic Regression, CatBoost, and a Keras neural network. The project compares modeling approaches and feature-screening signals rather than presenting a validated HR decision product.

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](./LICENSE)

## Problem and approach

The goal is to estimate an employee attrition-risk class from structured HR features. The model branches explore:

- **Logistic Regression:** a statistical baseline with regularization and class-weight/threshold tuning.
- **CatBoost:** gradient-boosted trees with parameter search and class weighting.
- **Neural Network:** a feed-forward Keras model for nonlinear feature interactions.
- **Feature triage:** triangulation of SHAP importance, permutation-based importance/AUC change, and VIF-based multicollinearity indicators.
- **Evaluation:** training/validation/test confusion matrices, ROC and precision-recall plots, threshold comparisons, and selected experiment tracking/export utilities.

The three branches are separate experiments and should be assessed using their own README, requirements, preprocessing and evaluation notes. Reported numbers are historical run outputs and have not been reproduced as part of this README pass.

## Model branches

| Branch | Implementation | Supporting documentation |
|---|---|---|
| CatBoost | `catboost/catboost_final.py` | [CatBoost README](./catboost/README.md) |
| Neural network | `neural network/regression_final.py` | [Neural-network README](./neural%20network/README.md) |
| Logistic Regression | `regression/regression_final.py` | [Logistic-regression README](./regression/README.md) |

Each branch includes its own `requirements.txt` and evaluation images. Install dependencies from the branch you intend to inspect rather than assuming a single environment covers all three.

## Data and execution requirements

**The HR dataset is not included in this repository snapshot.** The model scripts load `/content/data_csv.csv`, a Google Colab-style path. You must provide an authorized dataset with the columns expected by the chosen branch and adjust the data path when running outside Colab.

The Python files are notebook exports and contain notebook-specific installation commands such as `!pip install`. They are not directly executable with an ordinary `python script.py` invocation without first removing/converting notebook syntax and configuring local paths. Open the relevant file as notebook cells in Colab or convert it into a conventional Python module before local use.

Typical branch workflow:

1. Open the branch directory and inspect its `requirements.txt` and README.
2. Prepare the approved HR dataset and verify its schema, target definition, missing values, and class distribution.
3. Run the preprocessing, split, training, validation, threshold-selection, and final test steps in the intended order.
4. Review the saved evaluation plots and model metrics. Do not use the test set to tune the threshold.

## Interpretation and limitations

- The repository snapshot does not include the source HR dataset, so results cannot be independently reproduced from the checked-in files alone.
- Metrics reported in the existing branch READMEs differ by model version and run. Compare them only after aligning dataset, split, preprocessing, threshold-selection policy, and metric definitions.
- The model interfaces add random noise/jitter to a displayed probability in the current code, so repeated UI probabilities may vary for the same inputs.
- SHAP and permutation importance describe model behavior on the selected dataset; they do not establish causal explanations or absence of bias.
- Employee data is sensitive. Use an approved, anonymized dataset and do not expose a public Gradio share URL with confidential inputs.
- This project is an educational engineering demonstration. It is not independently validated for hiring, promotion, retention, termination, or other employment decisions. It must not be used as the sole basis for decisions about people.

## Repository contents

```text
AttritionX: Triangulated ML Pipeline for Employee Attrition Prediction/
├── README.md
├── catboost/
│   ├── catboost_final.py
│   ├── requirements.txt
│   ├── README.md
│   └── evaluation plots
├── neural network/
│   ├── regression_final.py
│   ├── requirements.txt
│   ├── README.md
│   └── evaluation plots
└── regression/
    ├── regression_final.py
    ├── requirements.txt
    ├── README.md
    └── evaluation plots
```

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

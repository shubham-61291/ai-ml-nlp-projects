# ⚡ AttritionX — Employee Attrition Prediction (Triangulated ML Framework)

This repository unifies three independent ML pipelines — **Logistic Regression**, **CatBoost**, and **Neural Network (Keras)** — designed to predict **employee attrition** using triangulated feature selection and explainable AI.  
Each model complements the other: Logistic Regression provides interpretability, CatBoost ensures boosting efficiency, and Neural Network captures non-linear relationships.

---

## 🚀 Project Overview
- **Objective:** Predict employee attrition using structured HR data  
- **Models Used:** Logistic Regression · CatBoost · Neural Network (Keras)  
- **Approach:** Triangulated feature selection (SHAP + Permutation + VIF)  
- **Output:** Clean evaluation reports and explainable visuals for each model  
- **Interface:** Interactive Gradio web app  

---

## 💡 Why CatBoost Was Chosen
CatBoost was selected as the **central model** in AttritionX due to its ability to handle categorical variables efficiently and deliver consistent generalization across validation folds.

| Advantage | Explanation |
|------------|-------------|
| **Handles Categorical Features Natively** | No need for one-hot encoding; avoids data leakage with ordered boosting. |
| **Stable AUC & Recall** | Consistently achieves balanced precision-recall across test folds. |
| **Interpretability via SHAP** | Produces clean, human-readable feature importance scores. |
| **Fast Convergence** | Requires fewer iterations and hyperparameters than XGBoost or LightGBM. |
| **Robust Under Class Imbalance** | Performs better than neural models when target distribution is skewed. |

In short, **CatBoost bridges the gap between statistical simplicity and deep-learning power**, making it the most balanced model for HR attrition analytics.

---

## 🖼️ Image Embeddings for Explainability
Each model generates visual outputs that are **embedded directly into reports** for interpretability and transparency.

| Visual Type | Purpose |
|--------------|----------|
| **Confusion Matrix** | Shows classification accuracy across true/false positives & negatives. |
| **ROC & PR Curves** | Illustrate model trade-offs and optimal threshold selection. |
| **SHAP Summary Plots** | Display feature impact magnitude and direction. |
| **Triangulation Charts** | Show features dropped based on SHAP, AUC, and VIF agreement. |

These embedded visuals ensure that every performance metric and feature importance result is **visually auditable**, allowing HR analysts to interpret “why” behind each prediction.

---

## 🧠 Model Structure

| Model | Core Technique | Key Strength | Performance Focus |
|--------|----------------|---------------|-------------------|
| Logistic Regression | Statistical Classification | High interpretability | Baseline calibration |
| CatBoost | Gradient Boosting on Decision Trees | Balanced precision-recall | Primary production model |
| Neural Network | Deep Feedforward (Keras) | Captures complex non-linearities | Enhanced recall stability |

---

## 📊 Evaluation Summary

| Dataset | Model | AUC | F1 | Recall | Threshold |
|----------|--------|-----|----|---------|------------|
| Validation | CatBoost | 0.836 | 0.57 | 0.58 | 0.48 |
| Validation | Neural Net | 0.815 | 0.55 | 0.54 | 0.55 |
| Validation | Logistic Regression | 0.84 | 0.52 | 0.54 | 0.63 |

All three models show **consistent validation behavior** with distinct trade-offs between interpretability and recall.

---

## 🧩 Future Enhancements
- Integrate **Optuna** for automated hyperparameter tuning  
- Build an **ensemble meta-model** combining outputs from all three models  
- Develop a **dashboard** for real-time attrition monitoring  
- Deploy via **Streamlit Cloud** or **Hugging Face Spaces**

---

## 👨‍💻 Author
**Shubham Singh**

---

## 📜 License
MIT License

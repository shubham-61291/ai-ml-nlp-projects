# ⚡ Neural Network — Employee Attrition Prediction (Triangulated Deep Learning Pipeline)

This project implements a **Neural Network (Keras–TensorFlow)** pipeline for predicting **employee attrition** using triangulated feature selection and threshold tuning.  
It combines explainability (SHAP + Permutation + VIF), MLflow tracking, and Gradio deployment for interactive inference.

---

## 🚀 Key Highlights
- Deep Feedforward Neural Network (2 hidden layers, ReLU + Dropout)  
- Grid search on **hidden units**, **learning rate**, and **class weights**  
- **Triangulated feature pruning**: SHAP + Permutation AUC Drop + VIF  
- **Threshold tuning** for F1 optimization  
- **Cross-validation parity** with Logistic and CatBoost pipelines  
- **MLflow integration** for parameter, metric, and artifact logging  
- **Gradio UI** with dual tabs — Prediction & Explainability  
- GPU acceleration (TensorFlow backend)

---

## 📊 Model Evaluation Results

### Confusion Matrices
![Confusion Matrix — Train (Final)](confusion_matrix_training.png)
![Confusion Matrix — Validation (Final)](confusion_matrix_validation.png)
![Confusion Matrix — Test (Final)](confusion_matrix_test.png)

---

### ROC & PR Curves
![ROC Curve — Train](roc_curve_training.png)
![ROC Curve — Validation](roc_curve_validation.png)
![ROC Curve — Test](roc_curve_test.png)
![Precision–Recall Curve](precision_recall_curve.png)
![PR Threshold Comparison](precision_recall_curve_threshold_comparison.png)
![ROC Threshold Comparison](roc_curve_threshold_comparison.png)

---

### Feature Importance & Triangulation
![SHAP Feature Importance (Final)](shap_feature_importance_final_triangulated.png)
![SHAP Validation Comparison](shap_feature_importance_validation_set.png)
![Feature Correlation Heatmap](feature_correlation_heatmap.png)
![Triangulation Flags per Feature](triangulation_flag_per_feature.png)
![SHAP vs Permutation Comparison](feature_importance_comparison_shap_vs_permutation.png)

---

## 💡 Insights
- **Best Config:** `hidden_units=128`, `lr=0.001`, `dropout=0.2`, `batch=64`, `epochs=30`, `class_weights=[1,2]`  
- **Triangulated Drop:** 8 features removed (≥2 flags)  
- **Validation AUC:** 0.815 → **0.793 (Final)**  
- **Test AUC:** 0.7703 | **Best-F1 threshold:** 0.553  
- **Validation F1:** 0.5778 → **0.591 (Tuned)**  
- Stable generalization across folds and no drift after retraining  

---

## 🧩 Future Enhancements
- Integrate **Optuna** for automatic hyperparameter search  
- Extend to **multiclass attrition segmentation**  
- Add **drift detection** with MLflow monitoring  
- Deploy model via **Streamlit Cloud** or **Hugging Face Spaces**

---

## ⚙️ Dependencies
Refer to `requirements.txt` for all dependencies.

---

## 👨‍💻 Author
**Shubham Singh**

---

## 📜 License
MIT License

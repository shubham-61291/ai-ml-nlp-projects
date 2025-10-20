AI–ML–NLP Projects

A collection of professional AI/ML/NLP projects showcasing applied machine learning, natural language processing, and generative AI in real-world educational and business contexts. These projects span content tagging, personalized retention scheduling, sentiment-driven churn prediction, and generative tutoring assistants.

📂 Projects
1. Automated Content Tagging Pipeline

An AI-powered system for tagging educational topics by subject and difficulty using TF-IDF + Logistic Regression (baseline) and DistilBERT (transformer).

📊 Outputs: classification reports, confusion matrices, subject predictions for adaptive learning.

🔗 Forms the foundation for retention scheduling models (MARS).

2. MARS – Memory & Retention Scheduling

An AI framework that models forgetting curves and recommends personalized review schedules.

⚙️ Approaches:

Log-linear regression (baseline)

Neural network (Keras/TensorFlow) predicting forgetting rate (λ).

📊 Outputs: recommended review dates, evaluation metrics (MAE, RMSE, R²).

3. MathsGPT & TeacherGPT

A generative math reasoning model fine-tuned on textbook problems, with an AI tutor interface.

🤝 MathsGPT: fine-tuned FLAN-T5 for step-by-step math solutions.

🧑‍🏫 TeacherGPT: wraps MathsGPT into a tutoring assistant with a Gradio interface.

📊 Features: few-shot prompting, beam search, and structured explanations.

4. Sentiment Analysis & Churn Rate Prediction

Analyzes NPS feedback data to classify sentiment and estimate churn.

⚙️ Models:

Logistic Regression + TF-IDF (baseline)

DistilBERT (transformer) with early stopping.

📊 Outputs: confusion matrices, loss curves, business KPIs (NPS, churn %, retention %).

🛠️ Tech Stack

Languages & Frameworks: Python, PyTorch, TensorFlow/Keras, Scikit-learn

Libraries: Hugging Face Transformers, Datasets, Accelerate, Matplotlib, Seaborn

Techniques: NLP classification, retention curve modeling, generative reasoning (T5), sentiment & churn analytics

5. 🧠 AttritionX – Employee Attrition Prediction

A triangulated ML framework to predict employee attrition using Logistic Regression, CatBoost, and Neural Networks (Keras).

⚙️ Approach:

Triangulated feature selection combining SHAP, Permutation Importance, and VIF.

Independent model pipelines with cross-validation, threshold tuning, and MLflow tracking.

Interactive Gradio interface for prediction and explainability.

📊 Highlights:

Logistic Regression → Statistical baseline for interpretability

CatBoost → Handles categorical features natively with stable recall

Neural Network → Deep model for non-linear HR patterns

Tuned thresholds and recall calibration for HR decision support

💡 Key Insight:
CatBoost was selected as the central model for its native categorical handling, stable AUC (≈ 0.83–0.84), and explainability via SHAP.
All models embed confusion matrices, ROC/PR curves, and SHAP plots directly into reports for visual interpretability.

👤 Author

Shubham Singh

📜 License

MIT License.

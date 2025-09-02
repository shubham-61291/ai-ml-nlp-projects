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

👤 Author

Shubham Singh

📜 License

MIT License.

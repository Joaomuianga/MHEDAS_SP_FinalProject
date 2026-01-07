## 🩺 End-to-End Diabetes Prediction System

This project implements a **collaborative, end-to-end machine learning system** for predicting diabetes using the **Pima Indians Diabetes Dataset**. The goal is to design a **modular, reproducible, and deployable pipeline**, covering the full lifecycle of a data science project: from data exploration and cleaning to model training, evaluation, API deployment, and user interaction.

The project is organized using **Git best practices**, where each component is developed in a dedicated branch and later merged into the main branch.

---

## 🧩 Project Architecture & Task Division

### 🔧 Person 1 — Git Management & Configuration

**Branch:** `feat/config-setup`
Responsible for project initialization and coordination.

**Responsibilities:**

* Initialize the GitHub repository and folder structure
* Create `config.py` to centralize configuration variables:

  * `DATA_PATH = "data/diabetes.csv"`
  * `MODELS_DIR = "models/"`
* Write and maintain `README.md` with setup and execution instructions
* Merge validated pull requests into the `main` branch

---

### 📊 Person 2 — Exploratory Data Analysis & Preprocessing

**Branch:** `feat/data-cleaning`
Focuses on understanding and cleaning the dataset.

**Responsibilities:**

* Perform Exploratory Data Analysis (EDA) in `src/EDA.py`

  * Generate and save **Correlation Matrix** and **Class Balance** plots in the `plots/` folder
* Identify and handle invalid or missing values
* Implement `load_and_clean_data(csv_path)` in `src/preprocess.py`
* Return a **cleaned Pandas DataFrame** ready for modeling
* Contribute EDA outputs to the final report

---

### 🤖 Person 3 — Model Training

**Branch:** `feat/model-training`
Builds and persists the machine learning model.

**Responsibilities:**

* Implement `train_and_save_model(df)` in `src/train.py`
* Import cleaned data from preprocessing
* Split the dataset into features (X) and target (y)
* Scale features for optimal model performance
* Train and compare multiple models:

  * Logistic Regression
  * Support Vector Machine
  * Random Forest
* Select the best-performing model
* Save trained artifacts:

  * `model.pkl`
  * `scaler.pkl`

---

### 📈 Person 4 — Model Evaluation

**Branch:** `feat/model-evaluation`
Generates metrics and visual outputs for reporting.

**Responsibilities:**

* Implement `evaluate_model(model_path, test_data)` in `src/evaluate.py`
* Load the trained model
* Generate predictions on test data
* Compute and print evaluation metrics (e.g., accuracy, ROC-AUC, F1-score)
* Generate and save confusion matrices and evaluation plots as PNG files
* Provide figures for the final written report

---

### 🌐 Person 5 — API Development

**Branch:** `feat/api-endpoint`
Exposes the model through a web service.

**Responsibilities:**

* Build a REST API using **FastAPI**
* Define a `PatientData` Pydantic model with the 8 clinical input variables
* Load `model.pkl` and `scaler.pkl` at application startup
* Implement endpoint:

  * `POST /predict`
* Return predictions in JSON format:

```json
{
  "diagnosis": "Diabetes",
  "probability": 0.82
}
```

---

### 🖥️ Person 6 — User Interface

**Branch:** `feat/frontend-ui`
Creates an interface for clinical use.

**Responsibilities:**

* Develop a web interface using **Streamlit**
* Create an interactive form with sliders and numeric inputs
* Send user input to the API endpoint (`http://localhost:8000/predict`)
* Display prediction results clearly for clinicians

---

### 📦 Person 7 — Deployment & Containerization

**Branch:** `feat/docker-deploy`
Ensures portability and reproducibility.

**Responsibilities:**

* Create `requirements.txt` listing all dependencies:

  * pandas, scikit-learn, fastapi, uvicorn, joblib, streamlit, requests
* Write a `Dockerfile`:

  * Base image: `python:3.9-slim`
  * Copy project files
  * Install dependencies
  * Run the API using Uvicorn
* Document Docker build and run commands in the README

---

## 🚀 Final Outcome

The final system is:

* **Modular** — each component is independently developed
* **Reproducible** — consistent results across environments
* **Deployable** — Dockerized API and UI
* **Production-ready** — suitable for real-world clinical integration

This project demonstrates strong practices in **scientific programming**, **machine learning engineering**, and **collaborative software development**.

---

**If you want**, I can:

* shorten this for a **1-page report**
* turn it into a **diagram (architecture flow)**
* adapt it to **course submission requirements**
* write the **README.md run instructions section**


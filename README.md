# Student Exam Performance Prediction

A Machine Learning web application that predicts a student's **Math Score** based on demographic information, parental education, lunch type, test preparation, reading score, and writing score.

The project covers the complete Machine Learning workflow — from Exploratory Data Analysis and preprocessing to model training, evaluation, deployment, and CI/CD using AWS.

## 🚀 Live Demo

[Student Exam Performance Prediction - Live Application](http://studentperformance-env.eba-7a4pfufd.ap-south-1.elasticbeanstalk.com/)

---

## 📌 Project Overview

The objective of this project is to predict a student's **Math Score** using other available student attributes.

The project follows a complete end-to-end Machine Learning pipeline:
* Data ingestion
* Exploratory Data Analysis (EDA)
* Data preprocessing
* Numerical feature scaling
* Categorical feature encoding
* Train-test splitting
* Multiple regression model training
* Model evaluation
* Hyperparameter tuning
* Best model selection
* Model and preprocessing object serialization
* Flask web application
* AWS Elastic Beanstalk deployment
* AWS CodePipeline CI/CD

---

## 📊 Dataset

The project uses the **Students Performance in Exams** dataset.

The dataset contains information about students including:
* Gender
* Race/Ethnicity
* Parental Level of Education
* Lunch
* Test Preparation Course
* Reading Score
* Writing Score
* Math Score

### Target Variable
* `math score`: The model predicts the student's Math Score.

### Input Features
The application uses the following features:
* `gender`
* `race/ethnicity`
* `parental level of education`
* `lunch`
* `test preparation course`
* `reading score`
* `writing score`

---

## 🔍 Exploratory Data Analysis

Exploratory Data Analysis was performed to understand the dataset and identify relationships between different variables.

The analysis included:
* Checking dataset structure and missing values
* Understanding categorical variables
* Distribution, univariate, and bivariate analysis
* Score distributions
* Relationship between reading, writing, and math scores
* Analysis based on gender and parental level of education
* Boxplots, violin plots, and correlation analysis

The EDA notebook is available in: `notebook/1. EDA STUDENT.ipynb`

---

## ⚙️ Data Preprocessing

The preprocessing pipeline handles both numerical and categorical features.

**Numerical Features:**
* `reading score`
* `writing score`
* **Transformations:** Median imputation, Standardization (`StandardScaler`)

**Categorical Features:**
* `gender`
* `race/ethnicity`
* `parental level of education`
* `lunch`
* `test preparation course`
* **Transformations:** Most-frequent imputation, One-Hot Encoding, Standardization

A `ColumnTransformer` applies the appropriate transformations, and the preprocessing object is saved as `artifacts/preprocessor.pkl`. This ensures the exact same preprocessing is applied during prediction.

---

## 🤖 Machine Learning Models

Multiple regression algorithms were evaluated based on their **R² Score**, including:
* Linear Regression
* Lasso Regression
* Ridge Regression
* Support Vector Regression
* K-Nearest Neighbors Regressor
* Decision Tree Regressor
* Random Forest Regressor
* AdaBoost Regressor
* XGBoost Regressor

---

## 🎯 Hyperparameter Tuning

Hyperparameter tuning was performed on selected models to improve performance. Examples of explored hyperparameters:

* **Random Forest:** `n_estimators`
* **Decision Tree:** `criterion`
* **AdaBoost:** `learning_rate`, `n_estimators`
* **XGBoost:** `learning_rate`, `n_estimators`

The tuned model with the highest evaluation performance was selected for the final application.

---

## 🔄 Machine Learning Pipeline

Dataset → Data Ingestion → Train-Test Split → Data Transformation 
→ Numerical Scaling & Categorical Encoding → Model Training 
→ Model Evaluation → Hyperparameter Tuning → Best Model Selection 
→ Model Serialization → Flask Application → AWS Elastic Beanstalk


## 📁 Project Structure

```text
student-performance-project/
│
├── .ebextensions/
│   └── python.config
├── artifacts/
│   ├── model.pkl
│   ├── preprocessor.pkl
│   ├── train.csv
│   └── test.csv
├── logs/
├── notebook/
│   ├── data/
│   │   └── StudPerf.csv
│   ├── 1. EDA STUDENT.ipynb
│   └── 2. MODEL TRAINING.ipynb
├── src/
│   ├── components/
│   │   ├── data_ingestion.py
│   │   ├── data_transformation.py
│   │   └── model_trainer.py
│   ├── pipeline/
│   │   ├── predict_pipeline.py
│   │   └── train_pipeline.py
│   ├── exception.py
│   ├── logger.py
│   └── utils.py
├── templates/
│   └── home.html
├── application.py
├── requirements.txt
├── setup.py
├── README.md
└── .gitignore

```

---

## 🧩 Project Components

**1. Data Ingestion** (`src/components/data_ingestion.py`)
Reads the dataset, creates artifacts, splits train/test datasets, and saves them to `artifacts/`.

**2. Data Transformation** (`src/components/data_transformation.py`)
Handles numerical and categorical imputation, scaling, one-hot encoding, and saves `preprocessor.pkl`.

**3. Model Training** (`src/components/model_trainer.py`)
Trains multiple algorithms, evaluates them, performs hyperparameter tuning, and saves the best model as `model.pkl`.

**4. Prediction Pipeline** (`src/pipeline/predict_pipeline.py`)
Loads the preprocessing object and trained model to generate predictions from new web inputs.

**5. Flask Application** (`application.py`)
Provides the web interface for users to enter student attributes and receive the predicted score.

---

## 🌐 Web Application & Deployment

The application is deployed using AWS Elastic Beanstalk with continuous integration via AWS CodePipeline.

**Deployment Architecture:**

```text
GitHub Repository → AWS CodePipeline → AWS Elastic Beanstalk (EC2) → Flask App

```

**AWS Services Used:**

* Elastic Beanstalk
* CodePipeline
* IAM
* EC2 (Managed by Elastic Beanstalk)

---

## 🛠️ Technologies Used

| Category | Tools/Libraries |
| --- | --- |
| **Language** | Python |
| **Data Analysis** | Pandas, NumPy |
| **Visualization** | Matplotlib, Seaborn |
| **Machine Learning** | Scikit-learn, XGBoost |
| **Web Framework** | Flask |
| **Serialization** | Dill |
| **Deployment** | AWS Elastic Beanstalk, CodePipeline, EC2, IAM |
| **Tools** | VS Code, Jupyter, Git, GitHub |

---

## 💻 How to Run Locally

**1. Clone the repository:**

```bash
git clone YOUR_GITHUB_REPOSITORY_URL
cd student-performance-project

```

**2. Create and activate a virtual environment:**

```bash
python -m venv venv

# Windows:
venv\Scripts\activate

# Mac/Linux:
source venv/bin/activate

```

**3. Install dependencies:**

```bash
pip install -r requirements.txt

```

**4. Run the Flask application:**

```bash
python application.py

```

Open the generated local URL in your browser to view the application.

---

## 📈 Future Improvements

* Improving the user interface and adding data visualizations
* Adding confidence or prediction ranges
* Experimenting with additional regression algorithms
* Implementing automated testing and Docker support
* Expanding the CI/CD workflow

---

## 👨‍💻 Author

**Animesh Sharma**

*B.Tech Computer Science Engineering Student*

[Github](https://github.com/Animessshh)
[LinkedIn](https://www.linkedin.com/in/animesh-sharma-b19443348/)

```

```



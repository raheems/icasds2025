
# Data Science in Industry Workshop – From Problem to Production

This repository contains all materials for a hands‑on workshop designed to help students and early‑career data scientists experience how real business problems are solved in industry using data science and machine learning.[^1]

The focus is not only on models, but on the full lifecycle: understanding a business problem, working with stakeholders, building a proof‑of‑concept (POC), and collaborating in teams to deliver impact, following an industry‑style workflow.[^1]

***

## 1. Background and Motivation

Most students learn machine learning through clean datasets and isolated algorithms, but real organizations rarely work that way. In practice:[^1]

- Problems start as vague business pains (“we are missing targets”, “this process is too slow”), not as neat Kaggle competitions.[^1]
- Multiple teams are involved: business leaders, domain experts, data engineers, and data scientists.[^1]
- Success is measured in financial or operational terms, not just accuracy or F1‑score.[^1]

This workshop simulates that reality. Participants see and then practice the **end‑to‑end process** of taking a messy business challenge, framing it as a data problem, building a POC model, and presenting results back to “stakeholders” in a structured, collaborative way.[^1]

***

## 2. Workshop Structure

The workshop is organized into four segments, mirroring how many industry projects actually unfold.[^1]

1. **Industry Perspective**
Short talk on how organizations notice inefficiencies, missed targets, or competitive disadvantages, and why they turn to data science to address them.[^1]
2. **POC Demonstration**
Live, end‑to‑end demo showing a data science workflow: loading data, basic exploratory analysis, feature engineering, building a simple model, and connecting results to business questions.[^1]
3. **Group Activity**
Participants form cross‑functional “project teams” and work on different parts of the same problem (EDA, feature engineering, modeling, or business evaluation), mimicking how roles split in real projects.[^1]
4. **Group Discussion**
Teams present their approach and findings, compare decisions, and reflect on trade‑offs between technical performance, interpretability, and business value.[^1]

***

## 3. Repository Contents

```text
.
├── README.md                     # This file
├── slides/
│   └── Industry_Problem_Solving_Framework.pptx
│   └── Drug_Development_Pipeline.pptx
├── notebooks/
│   ├── Demo.ipynb                # Short live-demo notebook (POC walkthrough)
│   └── End_to_End.ipynb          # Full hands-on notebook (EDA + modeling + deep dive)
└── data/
    └── clinicaltrials_1000_cancer.csv   # Downloaded offline dataset for students
```

- **`slides/Industry_Problem_Solving_Framework.pptx`** – Presentation explaining industry context, the 11‑stage workflow, stakeholder roles, and a high‑level outline of the workshop.[^1]
- **`notebooks/Demo.ipynb`** – A compact notebook optimized for a 10–15 minute live demonstration of the workflow: reading the CSV, basic EDA, a simple model, and quick interpretation.[^1]
- **`notebooks/End_to_End.ipynb`** – A detailed notebook for students with step‑by‑step sections: data loading, EDA, feature engineering, stratified descriptive summaries (including `tableone`), multiple models (logistic regression, XGBoost, and templates for more), evaluation, explanations, and space for further experiments.[^1]
- **`data/clinicaltrials_1000_cancer.csv`** – A snapshot of ~1000 clinical trial records downloaded using the ClinicalTrials.gov v2 API, so the workshop can run completely offline.[^2][^3]

***

## 4. Problem Overview (High-Level)

The central use case in this workshop is framed as a **binary prediction problem**: given information about individual trials, predict whether they are likely to be **“successful”** (higher enrollment) or **“at risk”** (lower enrollment) according to a simple, transparent label definition.[^1]

Key aspects highlighted:

- **Problem framing** – Turning “we are losing money due to inefficiency” into a measurable question such as “which upcoming trials are likely to struggle so we can intervene early?”.[^1]
- **Label design** – Using a threshold‑based success indicator (e.g., above/below median enrollment) to create a supervised learning target for classification.[^1]
- **Features** – Combining categorical context (phase, overall status), simple counts (number of locations/countries), and derived indicators (multinational flag, optional duration) to model success.[^1]

The domain is intentionally simplified so students can focus on process and reasoning, not only on tiny performance gains.[^1]

***

## 5. Technical Components Covered

The notebooks walk through an end‑to‑end data science workflow, including:

- **Data loading** – Reading the offline CSV exported from the ClinicalTrials.gov API and inspecting structure and missingness.[^1]
- **Exploratory Data Analysis (EDA)** – Plotting distributions, relationships between features and target, and discussing outliers and skew.[^1]
- **Feature Engineering** – Cleaning categorical variables, constructing numeric counts, adding a multinational flag, and optionally approximating trial duration from dates.[^1]
- **Descriptive Stratified Summary** – Using the `tableone` Python library to create a “Table 1” describing features stratified by the binary outcome (success vs non‑success).[^1]
- **Modeling**
    - Baseline **Logistic Regression** with preprocessing via `ColumnTransformer` and `Pipeline`.[^1]
    - **XGBoost** classifier as a more flexible tree‑based model, with students encouraged to tune parameters.[^1]
    - Template code for additional models (Random Forest, GridSearchCV, partial dependence, SHAP) for deeper exploration.[^1]
- **Evaluation** – Classification reports, ROC AUC, confusion matrices, ROC curves, and cross‑validated scores to compare models.[^1]
- **Explanation \& Error Analysis** – Coefficient inspection for logistic regression, feature importance for tree‑based models, and simple error analysis of false positives/negatives.[^1]

***

## 6. Intended Audience

- Senior undergraduates, master’s students, or early‑career professionals in data science, statistics, or related fields.[^1]
- Participants should be comfortable with Python, `pandas`, and basic supervised learning, but no prior industry experience is assumed.[^1]

The workshop is designed for contexts where students may not yet have direct exposure to large tech or multinational companies, but want to learn **how industry teams think and work** on real problems.[^1]

***

## 7. Setup and Installation

You can run the notebooks either in **Google Colab** or **locally**.

### 7.1. Clone the Repository

```bash
git clone https://github.com/<your-org>/<your-repo>.git
cd <your-repo>
```


### 7.2. Local Environment (optional but recommended)

```bash
# Example with conda
conda create -n ds-workshop python=3.10
conda activate ds-workshop
pip install -r requirements.txt
```

`requirements.txt` includes packages such as `pandas`, `numpy`, `scikit-learn`, `xgboost`, `matplotlib`, `seaborn`, and `tableone`.[^1]

***

## 8. How to Run the Notebooks

### Option A – Google Colab (recommended for students)

1. Open GitHub and navigate to `notebooks/Demo.ipynb` or `notebooks/End_to_End.ipynb`.
2. Open in Colab (or download and upload the notebook to Colab).
3. Upload `data/clinicaltrials_1000_cancer.csv` to the Colab environment or mount Google Drive and adjust the file path in the notebook if needed.

The notebooks assume the CSV is available in a `data/` folder relative to the notebook (e.g., `../data/clinicaltrials_1000_cancer.csv`). You can tweak the path at the top of the notebook to match your setup.[^1]

### Option B – Local Jupyter / VS Code

```bash
jupyter notebook notebooks/Demo.ipynb
# or
jupyter notebook notebooks/End_to_End.ipynb
```

Run cells from top to bottom. Students can modify or add cells using the provided template code for additional models and analyses.[^1]

***

## 9. Suggested Group Activities

To simulate an industry project, split participants into cross‑functional teams and have them collaborate inside `End_to_End.ipynb`:

- **Team A – EDA \& Data Quality**
Explore distributions, identify data issues, and propose simple cleaning or transformation rules.[^1]
- **Team B – Feature Engineering**
Design and implement new features (e.g., categorical groupings, interaction terms), then test their impact on a baseline model.[^1]
- **Team C – Modeling \& Evaluation**
Add new models (Random Forest, tuned XGBoost, etc.), run hyperparameter search, and prepare a comparison of performance metrics.[^1]
- **Team D – Business Storytelling**
Take the modelling results and build a short “stakeholder narrative” explaining key drivers, risks, and recommended actions in non‑technical language.[^1]

Each team presents a short summary at the end, reinforcing the idea that real projects require collaboration and communication, not just solo coding.[^1]

***

## 10. Learning Objectives

By the end of this workshop, participants should be able to:

- Describe the main stages of an industry‑style data science project, from business problem to production‑oriented thinking.[^1]
- Frame vague business complaints as clear, measurable ML problems with success criteria.[^1]
- Implement a minimal but realistic end‑to‑end analysis pipeline in a notebook: data loading, cleaning, exploration, feature engineering, modeling, evaluation, and interpretation.[^1]
- Work effectively in small groups, taking on different roles similar to real data science teams.[^1]
- Communicate model results in language that business stakeholders can understand and act on.[^1]

***

<div align="center">⁂</div>

[^1]: image.jpg

[^2]: https://clinicaltrials.gov/data-api/api

[^3]: https://stackoverflow.com/questions/78415818/how-to-get-full-results-with-clinicaltrials-gov-api-in-python


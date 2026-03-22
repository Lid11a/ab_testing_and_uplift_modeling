# A/B testing and uplift modeling

A machine learning and experimentation project focused on evaluating the effect of a marketing campaign 
on user conversion and exploring whether treatment allocation can be improved through uplift modeling.

---

## Project status

This project is currently in the **research / notebook stage**.

The repository presently contains the exploratory and analytical part of the work implemented in a 
Jupyter notebook.  
A more structured engineering implementation is planned next, including modular project code, 
reusable utilities, logging, and test coverage.

---

## Table of contents

- [Project objective](#project-objective)
- [Project snapshot](#project-snapshot)
- [Main findings](#main-findings)
- [Project structure](#project-structure)
- [Project setup and execution](#project-setup-and-execution)
- [Technologies used](#technologies-used)
- [License](#license)

---

## Project objective

The goal of the project is twofold:

- estimate the average treatment effect of a marketing intervention using a classical A/B testing framework;
- evaluate whether user-level treatment heterogeneity can be used to improve targeting through uplift modeling.

In addition, the project examines whether CUPED can improve estimation efficiency for a noisy 
post-treatment business metric such as spend.

---

## Project snapshot

Current notebook-based analysis includes:

- data loading and initial quality checks;
- descriptive analysis of experimental groups;
- binary A/B test setup for treatment vs control;
- pre-treatment balance diagnostics;
- conversion effect estimation with confidence intervals and hypothesis testing;
- minimum detectable effect and sample size diagnostics;
- spend distribution analysis;
- CUPED-based variance reduction for spend;
- uplift modeling with T-, S-, and X-learners;
- model comparison based on the Qini coefficient and related uplift diagnostics.

---

## Main findings

At the current stage, the analysis supports the following conclusions:

- the Mens E-Mail campaign shows a statistically significant positive effect on conversion relative to the control group;
- CUPED is implemented correctly but provides negligible practical benefit for spend in this dataset because the selected pre-treatment covariate has very weak explanatory power;
- uplift modeling suggests the presence of heterogeneous treatment effects, meaning that more efficient targeting may be possible than under a uniform treatment policy.

---

## Repository structure

```
ab_testing_and_uplift_modeling/
├── data/
│   └── hillstrom_data/                  # downloaded locally via Kaggle API (not tracked in git)
├── notebooks/
│   └── ab-testing-cuped-uplift.ipynb
├── .gitignore                           # Git ignore rules
├── README.md                            # Project description
├── requirements.txt                     # Project dependencies
└── LICENSE                              # Project license
```

---

## Project setup and execution

### 1) Clone the repository

```
git clone https://github.com/lid11a/ab_testing_and_uplift_modeling.git
cd ab_testing_and_uplift_modeling
```

### 2) Kaggle API token setup (one-time)

The dataset is automatically downloaded using the Kaggle API.

- **Windows:** `%USERPROFILE%\.kaggle\kaggle.json`
- **Linux / macOS:** `~/.kaggle/kaggle.json`

For Linux / macOS, file permissions must be set as follows:

```
 chmod 600 ~/.kaggle/kaggle.json
```

### 3) Create and activate a virtual environment, then install dependencies

**Windows (PowerShell)**

```
python -m venv .venv
.venv\Scripts\activate
pip install -r requirements.txt
```

**macOS / Linux**

```
python -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
```

### 4) Run the notebook

Launch Jupyter Notebook or Jupyter Lab and execute the notebook
`ab_testing_cuped_uplift_modeling.ipynb` sequentially from top to bottom.

---

## Technologies used

- Python
- pandas
- numpy
- scipy
- scikit-learn
- statsmodels
- xgboost
- matplotlib
- seaborn
- Jupyter Notebook
- Kaggle API

---

## License

This project is licensed under the MIT License.
# LING 539 Class Competition: Movie Review Classifier

This repository contains all code for the LING 539 class-wide Kaggle competition. The task is to classify text documents into one of three categories:

- **Label 0**: Not a movie or TV show review
- **Label 1**: A positive movie or TV show review
- **Label 2**: A negative movie or TV show review

The competition is evaluated using macro F1 score and is hosted at:
https://www.kaggle.com/competitions/ling-539-competition-2026

## Repository Structure

```
.
├── scripts/                                    # Jupyter notebooks for EDA and modeling
│   ├── eda.ipynb                               # Exploratory data analysis
│   ├── [final_submission]model_lr.ipynb        # Tuned Logistic Regression (best model)
│   ├── model_nb.ipynb                          # Naive Bayes classifier
│   ├── model_svm.ipynb                         # Linear SVM classifier
│   ├── eda_plots.png                           # EDA visualization
│   └── README.md                               # Details on each notebook
├── submissions/                                # Generated submission CSV files for Kaggle
├── Dockerfile                                  # Docker configuration for containerized runs
├── requirements.txt                            # Python dependencies
├── .gitignore                                  # Specifies files not tracked by Git
├── sample_submission.csv                       # Sample submission format from Kaggle (local only)
├── train.csv                                   # Training data from Kaggle (local only)
└── test.csv                                    # Test data from Kaggle (local only)
```

## Data

The dataset is provided by the Kaggle competition and consists of three CSV files:

- `train.csv` -- 70,317 labeled training examples with columns `ID`, `TEXT`, and `LABEL`
- `test.csv` -- 17,580 unlabeled test examples with columns `ID` and `TEXT`
- `sample_submission.csv` -- sample submission file showing the required format

**Important:** `train.csv`, `test.csv`, and `sample_submission.csv` are listed in `.gitignore` and are not tracked by this repository. You must download them manually from the Kaggle competition page and place them in the root of this repository before running any notebooks.

To download the data:
1. Go to https://www.kaggle.com/competitions/ling-539-competition-2026
2. Navigate to the Data tab
3. Download `train.csv`, `test.csv`, and `sample_submission.csv`
4. Place all three files in the root of this repository

## Installation

1. Clone this repository:
```
git clone https://github.com/uazhlt-ms-program/grad-level-term-project-kaggle-competition-vivthuyh
cd grad-level-term-project-kaggle-competition-vivthuyh
```

2. Create and activate a virtual environment:
```
python -m venv venv
source venv/bin/activate  # on Windows: venv\Scripts\activate
```

3. Install dependencies:
```
pip install -r requirements.txt
```

4. Launch Jupyter:
```
jupyter notebook
```

## Running the Notebooks

Run the notebooks in the following order to reproduce results:

1. `scripts/eda.ipynb` -- explores the dataset and generates `eda_plots.png`
2. `scripts/[final_submission]model_lr.ipynb` -- trains and tunes the Logistic Regression model and generates the best submission file
3. `scripts/model_nb.ipynb` -- trains the Naive Bayes baseline model
4. `scripts/model_svm.ipynb` -- trains the Linear SVM model

Submission files are saved to the `submissions/` directory.

## Results

| Model | CV Macro F1 | Kaggle F1 |
|---|---|---|
| Naive Bayes | 0.8948 | -- |
| Logistic Regression (default) | 0.9197 | 0.9225 |
| LinearSVC | 0.9200 | 0.9208 |
| Logistic Regression (tuned, C=10) | 0.9238 | 0.9256 |

Best Kaggle submission: **submission_lr_2** with a macro F1 score of **0.9256**.

## Dependencies

See `requirements.txt` for the full list of dependencies. Key packages:

- `scikit-learn` -- machine learning models and evaluation
- `pandas` -- data loading and manipulation
- `numpy` -- numerical operations
- `matplotlib` / `seaborn` -- data visualization
- `jupyter` -- notebook environment

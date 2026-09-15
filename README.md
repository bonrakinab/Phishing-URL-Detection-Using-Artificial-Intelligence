# Phishing URL Detection Using Artificial Intelligence

A machine-learning study of **phishing URL detection** using classical classifiers and transformer-based language models. The project explores how URL/text representations, class balancing, and pretrained transformer models can be used to distinguish phishing links from legitimate URLs.

## Problem

Phishing links are deliberately designed to resemble trustworthy web addresses. Static blocklists can miss newly created attacks, so this project investigates supervised learning approaches that can learn patterns associated with phishing URLs and generalize to unseen samples.

## Dataset

The experiments use the **PhiUSIIL phishing URL dataset**, containing approximately **235,795 samples**.

The broader project evaluates conventional machine-learning and transformer-based approaches. This repository snapshot contains experiment notebooks for:

- BERT
- ALBERT
- Decision Tree
- Logistic Regression
- Decision Tree with SMOTE
- Logistic Regression with SMOTE

## Experimental workflow

```text
PhiUSIIL data
     │
     ▼
Cleaning / preparation
     │
     ├── Classical ML path
     │      ├── feature representation
     │      ├── optional SMOTE balancing
     │      └── classifier training
     │
     └── Transformer path
            ├── tokenization
            ├── pretrained language model
            └── fine-tuning / evaluation
     │
     ▼
Precision · Recall · F1 · Accuracy
```

## Approaches explored

### Classical machine learning

The repository contains Decision Tree and Logistic Regression experiments, including versions that apply **SMOTE (Synthetic Minority Over-sampling Technique)** to study the effect of class balancing.

### Transformer models

The repository includes experiments with **BERT** and **ALBERT**, treating URL/text classification as a transformer-based sequence-classification problem.

The original project work also compared additional machine-learning / transformer variants. The notebooks committed here are the reproducible experiment artifacts currently available in this repository.

## Reported results

The original project summary reports **over 99% precision, recall, and F1-score for the strongest evaluated models**, with BERT among the best-performing approaches.

Because individual notebooks represent separate experiments and configurations, results should be interpreted together with each notebook's train/test split, preprocessing, and model settings rather than as a single universal benchmark.

## Repository structure

```text
Phishing-URL-Detection-Using-Artificial-Intelligence/
├── BERT on PhiUSIIL Dataset.ipynb
├── BERT.ipynb
├── ALBERT.ipynb
├── Decision Tree.ipynb
├── Decision Tree using SMOTE.ipynb
├── Logistic Regression.ipynb
├── Logistic Regression with SMOTE.ipynb
└── README.md
```

## Running the experiments

The notebooks can be opened in **Jupyter Notebook**, **JupyterLab**, or **Google Colab**.

A typical local environment will require packages from the Python data-science and transformer ecosystem, such as:

```bash
pip install pandas numpy scikit-learn imbalanced-learn matplotlib transformers torch jupyter
```

Exact package versions may vary between notebooks because the project was developed as a collection of experiments rather than a packaged Python application.

## Key techniques

- Supervised binary classification
- URL/text preprocessing
- TF-IDF-style classical feature pipelines
- SMOTE class balancing
- Transformer tokenization
- BERT-family fine-tuning
- Precision, recall, F1-score, and accuracy evaluation

## Why compare classical ML and transformers?

Classical models are lightweight, interpretable, and quick to train. Transformer models can learn richer representations directly from token sequences but are significantly more computationally expensive. Comparing both approaches helps expose the trade-off between model complexity and predictive performance.

## Limitations

- Dataset performance does not guarantee equivalent performance on live web traffic.
- Phishing tactics evolve over time, creating dataset drift.
- A URL classifier should not be treated as a complete browser-security system.
- The repository currently contains research notebooks rather than a production inference service.
- Very high benchmark scores should always be checked for split strategy, duplicate leakage, and dataset-specific artifacts before deployment.

## Future improvements

- Consolidate preprocessing into a reproducible pipeline
- Add a `requirements.txt` with pinned versions
- Add Random Forest / additional transformer notebooks used in the broader study
- Add cross-validation and leakage checks
- Evaluate on a second, temporally separated phishing dataset
- Add explainability for classical models
- Package the best model behind a small API or web interface
- Add adversarial and shortened-URL evaluation

## Tech stack

- **Language:** Python
- **Classical ML:** scikit-learn
- **Class balancing:** SMOTE / imbalanced-learn
- **Transformers:** BERT, ALBERT
- **Environment:** Jupyter / Google Colab
- **Domain:** cybersecurity, phishing detection, NLP, machine learning

---

This repository documents an experimental comparison of traditional machine-learning and transformer approaches for phishing URL classification.

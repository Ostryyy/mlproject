# Student Performance – End-to-End ML (Flask + scikit-learn) 🇬🇧

An end-to-end **Machine Learning** project that predicts a student’s **math score** (`math_score`) using demographic features and the **reading** and **writing** scores (`reading_score`, `writing_score`).

This repository includes:
- notebooks for **EDA** and **model training**,
- an ML pipeline (Data Ingestion → Data Transformation → Model Trainer),
- a **Flask** web app with a form-based prediction UI,
- saved artifacts (`artifacts/model.pkl`, `artifacts/preprocessor.pkl`) ready for inference.

---

## Features

- Predicts `math_score` from:
  - `gender`
  - `race_ethnicity`
  - `parental_level_of_education`
  - `lunch`
  - `test_preparation_course`
  - `reading_score`
  - `writing_score`
- Data preprocessing:
  - missing value imputation (median / most_frequent),
  - one-hot encoding for categorical features,
  - feature scaling/standardization.
- Model comparison (in the training notebook) including: Linear/Ridge/Lasso, KNN, RandomForest, XGBoost, CatBoost, AdaBoost.
- Simple HTML UI (Flask templates) to enter input data and show the prediction result.

---

## Results (from the notebook)

In `notebook/2. MODEL TRAINING.ipynb`, several models were evaluated. Example **test R²** scores:

- Ridge Regression: **~0.8806**
- Linear Regression: **~0.8803**
- Random Forest Regressor: **~0.8512**
- CatBoosting Regressor: **~0.8516**

> Note: the artifacts stored in `artifacts/` may come from a different training run than the notebook outputs.

---

## Quickstart (run the Flask app)

### 1) Requirements
- Python 3.13+ (tested locally on 3.13.5)
- pip

### 2) Install dependencies
```bash
cd student-performance-main

python -m venv .venv

pip install -r requirements.txt
```

### 3) Start the app
```bash
python application.py
```

Open:
- `http://127.0.0.1:5000/` (landing page)
- `http://127.0.0.1:5000/predictdata` (prediction form)

---

## Train the model from scratch (pipeline)

The dataset is located at: `notebook/data/stud.csv`.

The training pipeline (entry in `src/components/data_ingestion.py`) performs:
1. load dataset,
2. save `artifacts/data.csv`,
3. split into `artifacts/train.csv` and `artifacts/test.csv`,
4. transform features and save `artifacts/preprocessor.pkl`,
5. train and save `artifacts/model.pkl`.

Run:
```bash
python -m src.components.data_ingestion
```

---

## Project structure

```
student-performance-main/
├─ application.py                 # Flask app (routes + templates)
├─ templates/
│  ├─ index.html
│  └─ home.html                   # prediction form
├─ notebook/
│  ├─ 1 . EDA STUDENT PERFORMANCE .ipynb
│  ├─ 2. MODEL TRAINING.ipynb
│  └─ data/stud.csv               # dataset
├─ artifacts/
│  ├─ model.pkl                   # trained model
│  ├─ preprocessor.pkl            # preprocessing pipeline (ColumnTransformer)
│  ├─ train.csv / test.csv / data.csv
├─ src/
│  ├─ components/
│  │  ├─ data_ingestion.py
│  │  ├─ data_transformation.py
│  │  └─ model_trainer.py
│  ├─ pipeline/
│  │  ├─ predict_pipeline.py      # PredictPipeline + CustomData
│  │  └─ train_pipeline.py
│  ├─ utils.py
│  ├─ logger.py
│  └─ exception.py
├─ requirements.txt
└─ setup.py                       # packaging (pip install -e .)
```

# Student Performance – End-to-End ML (Flask + scikit-learn) 🇵🇱

Projekt end-to-end **Machine Learning**, który przewiduje **wynik z matematyki** ucznia (`math_score`) na podstawie cech demograficznych oraz wyników z **czytania** i **pisania** (`reading_score`, `writing_score`).

W repozytorium znajdują się:
- notebooki do **EDA** i **trenowania modeli**,
- pipeline ML (Data Ingestion → Data Transformation → Model Trainer),
- aplikacja webowa **Flask** z formularzem do predykcji,
- zapisane artefakty (`artifacts/model.pkl`, `artifacts/preprocessor.pkl`) gotowe do inferencji.

---

## Funkcjonalności

- Predykcja `math_score` na podstawie:
  - `gender`
  - `race_ethnicity`
  - `parental_level_of_education`
  - `lunch`
  - `test_preparation_course`
  - `reading_score`
  - `writing_score`
- Przetwarzanie danych:
  - imputacja braków (median / most_frequent),
  - one-hot encoding dla cech kategorycznych,
  - skalowanie/standaryzacja.
- Porównanie modeli (w notebooku) m.in.: Linear/Ridge/Lasso, KNN, RandomForest, XGBoost, CatBoost, AdaBoost.
- Prosty interfejs HTML (Flask templates) do wprowadzania danych i wyświetlania wyniku.

---

## Wyniki (z notebooka)

W `notebook/2. MODEL TRAINING.ipynb` porównano kilka modeli. Przykładowe wartości **R² na teście**:

- Ridge Regression: **~0.8806**
- Linear Regression: **~0.8803**
- Random Forest Regressor: **~0.8512**
- CatBoosting Regressor: **~0.8516**

> Uwaga: artefakty w `artifacts/` mogą pochodzić z innego uruchomienia niż wyniki z notebooka.

---

## Szybki start (uruchomienie aplikacji Flask)

### 1) Wymagania
- Python 3.13+ (testowane lokalnie na 3.13.5)
- pip

### 2) Instalacja zależności
```bash
cd student-performance-main

python -m venv .venv

pip install -r requirements.txt
```

### 3) Start aplikacji
```bash
python application.py
```

Aplikacja:
- `http://127.0.0.1:5000/` (strona startowa)
- `http://127.0.0.1:5000/predictdata` (formularz predykcji)

---

## Trenowanie modelu od zera (pipeline)

Zbiór danych znajduje się w: `notebook/data/stud.csv`.

Pipeline (wejście w `src/components/data_ingestion.py`) wykonuje:
1. wczytanie danych,
2. zapis `artifacts/data.csv`,
3. podział na `artifacts/train.csv` i `artifacts/test.csv`,
4. transformacje i zapis `artifacts/preprocessor.pkl`,
5. trening i zapis `artifacts/model.pkl`.

Uruchom:
```bash
python -m src.components.data_ingestion
```

---

## Struktura projektu

```
student-performance-main/
├─ application.py                 # Flask app (routing + templates)
├─ templates/
│  ├─ index.html
│  └─ home.html                   # formularz predykcji
├─ notebook/
│  ├─ 1 . EDA STUDENT PERFORMANCE .ipynb
│  ├─ 2. MODEL TRAINING.ipynb
│  └─ data/stud.csv               # dane
├─ artifacts/
│  ├─ model.pkl                   # wytrenowany model
│  ├─ preprocessor.pkl            # preprocessing (ColumnTransformer)
│  ├─ train.csv / test.csv / data.csv
├─ src/
│  ├─ components/
│  │  ├─ data_ingestion.py
│  │  ├─ data_transformation.py
│  │  └─ model_trainer.py
│  ├─ pipeline/
│  │  ├─ predict_pipeline.py      # PredictPipeline + CustomData
│  │  └─ train_pipeline.py
│  ├─ utils.py
│  ├─ logger.py
│  └─ exception.py
├─ requirements.txt
└─ setup.py                       # paczkowanie (pip install -e .)
```

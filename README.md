# 🏠 House Price Prediction using Machine Learning

![Python](https://img.shields.io/badge/Python-3.12%2B-blue?logo=python&logoColor=white)
![License](https://img.shields.io/badge/License-MIT-green.svg)
![Status](https://img.shields.io/badge/Status-Completed-brightgreen)
![ML](https://img.shields.io/badge/Machine%20Learning-Regression-orange)
![scikit--learn](https://img.shields.io/badge/scikit--learn-1.3%2B-F7931E?logo=scikitlearn&logoColor=white)
![XGBoost](https://img.shields.io/badge/XGBoost-2.0%2B-red)

A complete, production-quality, end-to-end **Machine Learning regression project** that predicts residential house prices from property features — built with industry best practices, clean architecture, and full documentation.

---

## 📌 Project Overview

This project trains and compares three regression algorithms — **Linear Regression**, **Random Forest**, and **XGBoost** — to predict a house's sale price from features such as living area, lot size, quality ratings, neighborhood, and more. It covers the **full ML lifecycle**: data preprocessing, feature engineering, model training, evaluation, visualization, model persistence, and interactive prediction.

## 🎯 Problem Statement

Home buyers, sellers, and real-estate platforms need a reliable way to estimate a fair market price for a property based on its measurable characteristics. Manual appraisal is slow, inconsistent, and expensive. This project builds a data-driven regression system to automate that estimate.

## 🎯 Objectives

- Build a clean, reusable preprocessing pipeline for tabular housing data
- Train and fairly compare multiple regression algorithms
- Quantify model performance using standard regression metrics
- Visualize data patterns, model performance, and errors
- Persist trained models for reuse without retraining
- Provide a simple CLI to predict new house prices interactively

## ✨ Features

- ✅ End-to-end pipeline: raw CSV → cleaned data → trained models → predictions
- ✅ Three regression algorithms trained and benchmarked side-by-side
- ✅ Automatic missing value handling, duplicate removal, and outlier filtering (IQR)
- ✅ Feature engineering (house age, remodel age, total square footage, total baths)
- ✅ Categorical encoding + feature scaling with leak-free train/test splitting
- ✅ 6 auto-generated visualizations saved as PNG files
- ✅ Automatic best-model selection based on R² score
- ✅ Models persisted with Joblib for instant reuse
- ✅ Interactive terminal-based prediction script with input validation
- ✅ Fully typed, documented, PEP8-compliant Python code
- ✅ No deep learning / no GPU required — runs on any laptop

## 🧠 Machine Learning Algorithms Used

| Algorithm | Type | Why It's Included |
|---|---|---|
| **Linear Regression** | Linear model | Fast, interpretable baseline |
| **Random Forest Regressor** | Ensemble (bagging) | Captures non-linear feature interactions, robust to outliers |
| **XGBoost Regressor** | Ensemble (gradient boosting) | State-of-the-art tabular performance, typically the strongest model |

## 📊 Dataset Information

The project ships with a **ready-to-use `dataset.csv`** (2,000+ rows) structured to mirror the well-known **Kaggle "House Prices - Advanced Regression Techniques" / Ames Housing** dataset schema, so the code runs immediately with no setup.

**Want to use the real Kaggle dataset instead?**
1. Go to: https://www.kaggle.com/datasets/shashanknecrothapa/ames-housing (or search "Ames Housing dataset" / "House Prices Advanced Regression Techniques" on Kaggle)
2. Download `train.csv`
3. Rename it to `dataset.csv`
4. Make sure it has a `SalePrice` column (rename the target column if needed)
5. Place it in the project's root folder, replacing the sample file
6. Re-run `train_model.py`

The preprocessing pipeline automatically adapts to extra/missing columns as long as a `SalePrice` target column is present.

**Included Features:**

| Feature | Description |
|---|---|
| LotArea | Lot size in square feet |
| OverallQual / OverallCond | Overall material quality / condition (1–10) |
| YearBuilt / YearRemodAdd | Construction year / last remodel year |
| TotalBsmtSF / GrLivArea | Basement / above-ground living area (sq ft) |
| FullBath / HalfBath | Bathroom counts |
| BedroomAbvGr / TotRmsAbvGrd | Bedrooms / total rooms above ground |
| Fireplaces / GarageCars / GarageArea | Amenity counts and sizes |
| PoolArea | Pool area (sq ft) |
| Neighborhood / HouseStyle / GarageType / ExterCond | Categorical property attributes |
| YrSold / MoSold | Sale date info |
| **SalePrice** | 🎯 Target variable |

## 🛠️ Technologies Used

- **Language:** Python 3.12+
- **Data Handling:** pandas, numpy
- **Visualization:** matplotlib
- **Machine Learning:** scikit-learn, xgboost
- **Model Persistence:** joblib

No TensorFlow, no PyTorch, no deep learning — this is a pure classical ML project.

## 🏗️ Project Architecture

```
HousePricePrediction/
│
├── dataset.csv                 # Input dataset
├── house_price_prediction.py   # Main entry point (interactive menu)
├── preprocessing.py            # Data cleaning, encoding, scaling, feature engineering
├── model_utils.py              # Model training, evaluation, saving/loading
├── visualization.py            # Plot generation (6 chart types)
├── train_model.py              # Orchestrates preprocessing → training → plots → saving
├── predict.py                  # Interactive CLI for new predictions
├── requirements.txt            # Python dependencies
├── README.md                   # This file
├── GUIDE.md                    # Extremely detailed beginner walkthrough
├── LICENSE                     # MIT License
├── .gitignore                  # Git ignore rules
├── model_comparison.csv        # Saved metrics table (generated after training)
├── saved_model.pkl             # Best model bundle (generated after training)
├── linear_model.pkl            # Linear Regression model (generated after training)
├── randomforest_model.pkl      # Random Forest model (generated after training)
├── xgboost_model.pkl           # XGBoost model (generated after training)
└── *.png                       # Generated visualizations
```

> **Note:** All files live in a single flat folder by design — no subfolders.

## ⚙️ Installation

```bash
# 1. Clone or download the project folder
git clone https://github.com/<your-username>/HousePricePrediction.git
cd HousePricePrediction

# 2. Create a virtual environment (recommended)
python -m venv venv
venv\Scripts\activate        # Windows
source venv/bin/activate     # macOS/Linux

# 3. Install dependencies
pip install -r requirements.txt
```

## 📋 Requirements

```
pandas>=2.0.0
numpy>=1.24.0
matplotlib>=3.7.0
scikit-learn>=1.3.0
xgboost>=2.0.0
joblib>=1.3.0
```

## ▶️ How to Run

**Option A — Guided menu (recommended for beginners):**
```bash
python house_price_prediction.py
```

**Option B — Run steps individually:**
```bash
# Train all models, generate plots, and save models
python train_model.py

# Predict a new house price interactively
python predict.py
```

## 🔮 How Prediction Works

1. `predict.py` loads `saved_model.pkl`, which bundles the **best model**, the fitted **scaler**, the fitted **label encoders**, and the exact **feature order** used during training.
2. It prompts you for each property detail (lot area, quality, rooms, neighborhood, etc.) in the terminal, validating each input.
3. It applies the **identical feature engineering and encoding** used during training (e.g., house age, total square footage).
4. It scales the input using the training-time scaler and feeds it to the model.
5. It prints the predicted sale price.

## 📈 Results

After training on the included sample dataset:

| Algorithm | MAE | RMSE | R² Score | Training Time |
|---|---|---|---|---|
| **XGBoost 🏆** | $17,344.35 | $22,159.79 | **0.9598** | 0.444s |
| Linear Regression | $20,885.30 | $26,297.20 | 0.9434 | 0.002s |
| Random Forest | $25,211.06 | $31,922.76 | 0.9165 | 2.222s |

**Best Model: XGBoost Regressor** — automatically selected and saved as `saved_model.pkl`.

> Exact numbers will vary slightly depending on the dataset used and random seed, and will regenerate in `model_comparison.csv` every time you run `train_model.py`.

## 📐 Evaluation Metrics

| Metric | Meaning |
|---|---|
| **MAE** (Mean Absolute Error) | Average absolute dollar difference between predicted and actual price |
| **MSE** (Mean Squared Error) | Average of squared errors — penalizes large errors more |
| **RMSE** (Root Mean Squared Error) | Square root of MSE, in the same units as price ($) |
| **R² Score** | Proportion of price variance explained by the model (closer to 1.0 is better) |

## 🖼️ Screenshots

After running `train_model.py`, the following PNG files are generated in the project folder:

- `price_distribution.png` — Distribution of house sale prices
- `correlation_heatmap.png` — Correlation heatmap of numeric features
- `feature_importance.png` — Top 15 most important features (best model)
- `prediction_vs_actual.png` — Predicted vs actual scatter plot
- `residual_plot.png` — Residuals vs predicted values
- `error_distribution.png` — Histogram of prediction errors

*(Add these images here in your GitHub README once generated, e.g. `![Feature Importance](feature_importance.png)`)*

## 🚀 Future Improvements

- Serve predictions via a **Flask** or **FastAPI** REST API
- Build an interactive **Streamlit** web app for non-technical users
- Containerize with **Docker** for portable deployment
- Deploy to **AWS / Azure / GCP / Render / Railway**
- Add **CI/CD** with GitHub Actions (auto-test on every push)
- Add **hyperparameter tuning** (GridSearchCV / Optuna)
- Add **k-fold cross-validation** for more robust evaluation
- Expand **feature engineering** (e.g., polynomial features, target encoding)

See `GUIDE.md` Section 19 for a detailed explanation of each.

## 🎓 Learning Outcomes

By completing this project, you will practice:
- Structuring a real-world, multi-file Python ML codebase
- End-to-end regression workflow: cleaning → engineering → training → evaluating
- Comparing multiple algorithms objectively using consistent metrics
- Data visualization for diagnosing model performance
- Model persistence and building a prediction interface
- Git/GitHub workflow for showcasing a project professionally

## 📄 Resume Description

> **House Price Prediction — Machine Learning Regression Project**
> Built an end-to-end ML pipeline in Python (pandas, scikit-learn, XGBoost) to predict house prices, including data cleaning, feature engineering, and outlier handling; trained and benchmarked Linear Regression, Random Forest, and XGBoost models, achieving an R² of 0.96 with XGBoost; automated model comparison, visualization, and persistence for reproducible predictions.

See `GUIDE.md` Section 16 for more ATS-friendly bullet point variations.

## 📜 License

This project is licensed under the [MIT License](LICENSE).

## 👤 Author

**Stellar Intelligence**
Machine Learning / Software Engineering Project

---

⭐ If you found this project useful, consider giving it a star on GitHub!

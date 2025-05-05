# ❤️ Heart Disease Prediction using K-Nearest Neighbors (KNN)

## 📌 Overview

This repository contains a machine learning project designed for an R&D healthcare company. The goal is to predict whether a patient is likely to develop heart disease in the future using anonymized clinical data from multiple hospitals.

## 🗂️ Dataset

The dataset includes 918 patient records with the following features:

- `Age`
- `Sex` (M/F)
- `ChestPainType` (ATA, NAP, ASY, TA)
- `RestingBP` (Resting Blood Pressure)
- `Cholesterol`
- `FastingBS` (Fasting Blood Sugar)
- `RestingECG` (ECG results)
- `MaxHR` (Maximum Heart Rate)
- `ExerciseAngina` (Y/N)
- `Oldpeak` (ST depression induced by exercise)
- `ST_Slope` (Slope of the peak exercise ST segment)
- `HeartDisease` (Target: 1 = Yes, 0 = No)

> ⚠️ Some records had invalid values (e.g., RestingBP = 0, Cholesterol = 0). These were cleaned before training the model.

## 🧰 Tools & Libraries

- Python
- Pandas & NumPy
- Matplotlib & Seaborn
- Scikit-learn

## ⚙️ Preprocessing Steps

- Handled missing or invalid values.
- Used **One-Hot Encoding** for categorical features: `Sex`, `ChestPainType`, `RestingECG`, `ExerciseAngina`, `ST_Slope`
- Normalized features using **MinMaxScaler**
- Performed **train-test split** (80:20)

## 📊 Exploratory Data Analysis

- Count plots for categorical variables
- Histograms and KDEs for continuous features
- Correlation heatmap
- Comparative analysis of features across heart disease vs non-heart disease cases

## 🤖 Model: K-Nearest Neighbors (KNN)

- **Training:** Used `GridSearchCV` to tune the value of `k`
- **Evaluation Metrics:**
  - Accuracy Score
  - Confusion Matrix
  - Classification Report

## ✅ Results

- KNN showed good performance and was easy to interpret for healthcare professionals.
- Best accuracy obtained with tuned `k` value using GridSearchCV.

## 🚀 How to Run

1. Clone this repo:
   ```bash
   git clone https://github.com/your-username/heart-disease-prediction-knn.git
   cd heart-disease-prediction-knn

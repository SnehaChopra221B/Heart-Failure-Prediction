# Heart Disease Prediction

> *Predict the likelihood of heart disease using patient health indicators and K-Nearest Neighbors (KNN) modeling.*

![Heart Health](https://img.shields.io/badge/healthcare-AI%20project-red?style=flat-square)
![Python](https://img.shields.io/badge/Python-3.9%2B-blue?logo=python&logoColor=white)
![scikit-learn](https://img.shields.io/badge/Machine%20Learning-scikit--learn-yellow?logo=scikit-learn)

---

## Overview

This project uses machine learning to **predict heart disease** using clinical features like age, blood pressure, cholesterol levels, and more. It is based on a dataset collected from multiple hospitals.

---

## Key Features

- KNN classifier with hyperparameter tuning (`GridSearchCV`)
- Data cleaning and preprocessing for real-world medical data
- Exploratory Data Analysis (EDA) with visualizations
- Feature selection based on correlation and domain knowledge
- Final model accuracy: **83.33%**

---

## Dataset Details

| Type            | Features                                                                 |
|-----------------|--------------------------------------------------------------------------|
| Numerical       | `Age`, `RestingBP`, `Cholesterol`, `FastingBS`, `MaxHR`, `Oldpeak`       |
| Categorical     | `Sex`, `ChestPainType`, `RestingECG`, `ExerciseAngina`, `ST_Slope`       |
| Target Variable | `HeartDisease` (0 = No, 1 = Yes)                                         |
| Samples         | 918 rows                                                                 |

 *Note: Cleaned dataset by replacing/imputing physiologically implausible values.*

---

## Methodology

### Exploratory Data Analysis
- Count plots and grouped visualizations for categorical features
- Correlation heatmaps to identify top predictive features

### Feature Selection
Selected features:
- `MaxHR`, `Oldpeak`, `ExerciseAngina_Y`
- `ST_Slope_Flat`, `ST_Slope_Up`

### Model Development
- **Algorithm**: `KNeighborsClassifier`
- **Scaler**: `MinMaxScaler`
- **Split**: 85% train / 15% test (`random_state=417`)
- **Tuning**: `GridSearchCV` on:
  - `n_neighbors`: 1–100
  - `metrics`: `minkowski`, `euclidean`, `manhattan`

**Best Parameters**: `n_neighbors=32`, `metric=minkowski`  
**Test Accuracy**: **83.33%**

---

## Results

| Feature           | Accuracy (KNN k=3) |
|-------------------|-------------------|
| ST_Slope_Up       | 84.06%            |
| ST_Slope_Flat     | 81.88%            |
| Final Model (KNN) | **83.33%**        |

---

## How to Run

1. **Clone the repository**  
   ```bash
   git clone https://github.com/<your-username>/heart-disease-prediction.git
   cd heart-disease-prediction

## Project Structure
```
heart-disease-prediction/
├── data/
│   └── heart.csv.xls              # Dataset
├── notebooks/
│   └── heart_disease_prediction.ipynb  # Jupyter notebook with analysis and model
├── README.md                      # This file
├── requirements.txt               # Python dependencies
```

## Installation
1. Create a virtual environment (optional but recommended):
   ```bash
   python -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate
   ```
2. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```

## requirements.txt
```
pandas
numpy
matplotlib
seaborn
scikit-learn
jupyter
```

## Future Improvements
- Explore additional algorithms (e.g., Random Forest, Logistic Regression) for potentially better performance.
- Incorporate feature engineering to create new features, such as interaction terms.
- Address class imbalance if present in the dataset.
- Validate the model with external datasets to ensure generalizability.

## Contributing
Contributions are welcome! Please follow these steps:
1. Fork the repository.
2. Create a new branch (`git checkout -b feature-branch`).
3. Commit your changes (`git commit -m 'Add some feature'`).
4. Push to the branch (`git push origin feature-branch`).
5. Open a Pull Request.

## License
This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

## Contact
For questions or feedback, please contact [your-email@example.com](mailto:your-email@example.com).


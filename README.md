
# Heart Disease Prediction

## Overview
This project aims to predict the likelihood of heart disease in patients using a dataset collected from multiple hospitals. The dataset includes anonymized patient information such as age, sex, chest pain type, resting blood pressure, cholesterol levels, and other medical attributes. The goal is to build a machine learning model to accurately classify whether a patient is likely to have heart disease based on these features.

## Dataset
The dataset (`heart.csv.xls`) contains 918 entries with 12 columns:
- **Numerical Features**: Age, RestingBP, Cholesterol, FastingBS, MaxHR, Oldpeak
- **Categorical Features**: Sex, ChestPainType, RestingECG, ExerciseAngina, ST_Slope
- **Target Variable**: HeartDisease (0 for no heart disease, 1 for heart disease)

### Data Cleaning
- Removed one entry with `RestingBP = 0` as it is physiologically implausible.
- Replaced `Cholesterol = 0` values with the median cholesterol value, calculated separately for patients with and without heart disease to preserve data integrity.
- Converted categorical variables into dummy variables using one-hot encoding, dropping the first category to avoid multicollinearity.

## Methodology
### Exploratory Data Analysis (EDA)
- Visualized the distribution of categorical features using count plots.
- Analyzed the relationship between categorical features and heart disease using grouped count plots.
- Generated correlation heatmaps to identify features strongly correlated with heart disease (threshold > 0.3).

### Feature Selection
Selected the following features based on correlation analysis and domain relevance:
- MaxHR
- Oldpeak
- ExerciseAngina_Y
- ST_Slope_Flat
- ST_Slope_Up
- Sex_M (initially tested but later excluded in hyperparameter tuning)

### Model Development
- **Algorithm**: K-Nearest Neighbors (KNN) Classifier
- **Preprocessing**: Applied `MinMaxScaler` to scale numerical features to the range [0, 1].
- **Train-Test Split**: 85% training, 15% testing (random_state=417).
- **Initial Model**: Tested individual features with KNN (k=3) to evaluate their predictive power.
- **Multi-Feature Model**: Combined selected features and scaled them for improved performance.
- **Hyperparameter Tuning**: Used `GridSearchCV` to optimize:
  - Number of neighbors (`n_neighbors`: 1 to 100)
  - Distance metrics (`minkowski`, `euclidean`, `manhattan`)
  - Best parameters: `n_neighbors=32`, `metric=minkowski`
  - Best cross-validation score: 83.31%
  - Test accuracy: 83.33%

## Results
- The final KNN model, with optimized hyperparameters, achieved a test accuracy of **83.33%**.
- Key features contributing to the model's performance include `ST_Slope_Up` (84.06% accuracy when used alone) and `ST_Slope_Flat` (81.88% accuracy).

## Requirements
To run the project, install the required Python packages:
```bash
pip install pandas numpy matplotlib seaborn scikit-learn
```

## How to Run
1. Clone the repository:
   ```bash
   git clone https://github.com/<your-username>/heart-disease-prediction.git
   ```
2. Place the dataset (`heart.csv.xls`) in the project directory.
3. Run the Jupyter notebook (`heart_disease_prediction.ipynb`) or Python script to execute the analysis and model training:
   ```bash
   jupyter notebook heart_disease_prediction.ipynb
   ```
4. Ensure all dependencies are installed (see Requirements).

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


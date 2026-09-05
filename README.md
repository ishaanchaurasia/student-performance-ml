# Student Performance Prediction

Predicting students' final mathematics grades using machine learning and exploring the factors associated with academic performance.

## About

This project explores the UCI Student Performance dataset and uses exploratory data analysis, correlation analysis, and Random Forest regression to predict students' final mathematics grades (G3).

A key focus of the project is comparing prediction performance with and without the first- and second-period grades (G1 and G2).

## Dataset

The project uses the **Student Performance** dataset from the UCI Machine Learning Repository.

The dataset contains information about students' demographic, social, family, school, and academic characteristics.

The mathematics dataset used in this project is:

`student-mat.csv`

### Dataset Citation

Cortez, P. (2008). Student Performance [Dataset]. UCI Machine Learning Repository.

DOI: https://doi.org/10.24432/C5TG7T

The dataset is licensed under CC BY 4.0.

## Project Workflow

1. Data exploration
2. Data quality checks
3. Exploratory data analysis
4. Correlation analysis
5. Random Forest regression
6. Model comparison with and without G1/G2
7. Error analysis and visualization

## Exploratory Analysis

The project investigates:

- Distribution of final grades
- Study time and final grades
- Previous failures and final grades
- Relationships between numerical variables and G3
- Correlation between different features and final grade

## Machine Learning Model

Random Forest Regression is used to predict the final grade (G3).

Categorical variables are handled using One-Hot Encoding, while preprocessing is placed inside a Scikit-learn Pipeline.

Hyperparameters are tuned using `RandomizedSearchCV` with 5-fold cross-validation.

The same train/test split is used for both model settings to make the comparison fair.

## Model Comparison

Two models are evaluated:

### Model A — Without G1 and G2

G1 and G2 are excluded from the features.

This tests how well the final grade can be predicted using other student information.

### Model B — With G1 and G2

G1 and G2 are included as features.

This represents a situation where previous-period grades are already available.

## Results

The models were evaluated using Mean Absolute Error (MAE), Mean Squared Error (MSE), and R².

| Model | MAE | MSE | R² |
|---|---:|---:|---:|
| Without G1/G2 | 2.9971 | 14.1506 | 0.3099 |
| With G1/G2 | 1.2118 | 4.1156 | 0.7993 |

The model including G1 and G2 performs substantially better.

This shows that previous-period grades contain strong information about the final grade. However, the model without G1 and G2 provides a more challenging test of whether other student characteristics can predict final performance.

## Error Analysis

The model without G1 and G2 has difficulty predicting some extreme final grades.

For example, several students with an actual final grade of 0 were predicted to have grades around 7–10.

Similarly, some high-performing students were substantially underestimated.

This indicates that the available features without G1 and G2 are not sufficient to accurately capture every student's final outcome.

## Limitations

- The dataset contains only 395 students.
- Some final-grade values are relatively rare.
- Extreme grades are difficult for the model to predict accurately.
- The results may not generalize to other schools or student populations.
- G1 and G2 are strongly related to G3 because they represent earlier-period grades.
- Removing G1 and G2 significantly reduces predictive performance.

## Conclusion

This project demonstrates an end-to-end machine learning workflow for regression, including data exploration, data quality analysis, exploratory visualization, correlation analysis, model training, hyperparameter tuning, and evaluation.

The comparison between models with and without G1 and G2 demonstrates the importance of feature selection and previous academic performance when predicting final grades.

While the model including G1 and G2 achieves a substantially higher R², the model without them represents a more difficult prediction problem and highlights the limitations of predicting final performance using only the other available student information.

## Technologies Used

- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Scikit-learn
- Jupyter Notebook

## Repository Structure

```text
student-performance-ml/
│
├── data/
│   └── student-mat.csv
│
├── notebooks/
│   ├── 01_data_exploration.ipynb
│   ├── 02_data_quality.ipynb
│   ├── 03_exploratory_data_analysis.ipynb
│   ├── 04_correlation.ipynb
│   └── 05_random_forest.ipynb
│
├── README.md
└── requirements.txt

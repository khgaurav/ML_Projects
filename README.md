# Assignment 04: Titanic Survival Prediction using Decision Trees

## What this project does

This project builds a Decision Tree model to predict the survival of passengers on the Titanic using the dataset `titanic.csv`.
- **Data Preprocessing & Cleaning**: Selecting features (`Pclass`, `Sex`, `Age`, `Fare`), encoding categorical columns with `LabelEncoder`, and filling missing values in `Age`.
- **Data Splitting**: Splitting into training (80%) and testing (20%) sets.
- **Model Training & Evaluation**: Training a `DecisionTreeClassifier` with `max_depth=3` to avoid overfitting, and calculating train and test accuracy.
- **Model Interpretation**: Visualizing the decision tree splits and feature importances.

## How to run the notebook

1. Open `Assignment_04.ipynb` in Jupyter Notebook, JupyterLab, or VS Code.
2. Make sure `titanic.csv` is in the same folder as the notebook.
3. Run the cells from top to bottom.
4. If needed, install the required packages using the `requirements.txt`:
   ```bash
   pip install -r requirements.txt
   ```

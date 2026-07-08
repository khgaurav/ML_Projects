# Assignment 03: WheelsBazaar Used-Car Price Prediction

## What this project does

This project uses the WheelsBazaar used-car dataset in `car details v4.csv` to build a multivariable linear regression model (using Ridge regression) that predicts the fair market price of a used car from its attributes.

The notebook:
- Loads and inspects the dataset (`car details v4.csv`)
- Prepares the features by handling missing values and one-hot encoding categorical variables
- Splits the dataset into training (80%) and test (20%) sets
- Fits a Ridge regression model on the log-transformed target price
- Reports the intercept, alpha parameter, and top feature coefficients
- Evaluates the model on unseen test data using $R^2$, MAE, and RMSE
- Estimates the fair market price for a sample custom car listing

## How to run the notebook

1. Open `Assignment_03.ipynb` in Jupyter Notebook or VS Code.
2. Make sure `car details v4.csv` is in the same folder as the notebook.
3. Run the cells from top to bottom.
4. If needed, install the required Python packages listed in `requirements.txt`.

Example:

```bash
pip install -r requirements.txt
jupyter notebook Assignment_03.ipynb
```

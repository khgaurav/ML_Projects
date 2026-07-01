# Assignment 02: Telco Monthly Charge Prediction

## What this project does

This project uses the cleaned Telco dataset in `telco.csv` to build a multivariable linear regression model that predicts a customer's monthly charge from their service bundle.

The notebook:
- loads and inspects the data
- defines the service features and target
- splits the data into training and test sets
- fits a multivariable linear regression model
- reports the intercept and service coefficients
- evaluates the model on unseen data
- compares the result with a simpler single-variable baseline

## How to run the notebook

1. Open `Assignment_02.ipynb` in Jupyter Notebook or VS Code.
2. Make sure `telco.csv` is in the same folder as the notebook.
3. Run the cells from top to bottom.
4. If needed, install the required Python packages listed in `requirements.txt`.

Example:

```bash
pip install -r requirements.txt
jupyter notebook Assignment_02.ipynb
```

## Brief summary of findings

The multivariable model fits the data very well.

- Base plan charge (intercept): about £24.97
- Strongest positive coefficient: `InternetService_Fiber optic` at about £24.95
- `StreamingTV` and `StreamingMovies` each add about £10 per month
- The model's test performance is very strong: R2 = 0.9988, MAE = 0.7886, RMSE = 1.0504
- The single-variable add-on-count baseline is much weaker: R2 = 0.7009, MAE = 14.2369, RMSE = 16.4551

Overall, knowing the exact services a customer has is far better than just knowing how many add-ons they have.

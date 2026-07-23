# Assignment 06: Household Energy Consumption Forecasting using LSTM

## What this project does

This project builds an LSTM model that takes the past 7 days of hourly power
readings and forecasts the next 24 hours of consumption, using the UCI
*Individual Household Electric Power Consumption* dataset
(`household_power_consumption.txt`).

- **Data Preprocessing & Gap Handling**: Time-based interpolation for the ~1.25%
  missing values, resampling minute readings to hourly means, and a `log1p`
  transform on the target to stabilize near-zero nighttime load.
- **Temporal Split**: Chronological train / validation / test split (test = final
  6 months), with `MinMaxScaler` fit **only** on the training data to prevent
  leakage.
- **Model Training & Evaluation**: A 2-layer LSTM (128 hidden units) trained with
  Adam + MSE on the GPU (CUDA if available), evaluated with MAPE against a
  seasonal-naive baseline.
- **Deployment Checks**: Single-forecast inference latency benchmark (< 500 ms
  target) and a residual-based anomaly-alerting rule (3σ over 2+ consecutive
  hours, false-alarm rate < 5%).

See `practical_questions_answers.md` for the point-by-point answers to the
assignment requirements.

## How to run the notebook

1. Open `LSTM_Sentiment_Classification.ipynb` in Jupyter Notebook, JupyterLab, or
   VS Code.
2. Download the dataset from the
   [UCI repository](https://archive.ics.uci.edu/dataset/235/individual+household+electric+power+consumption)
   and place `household_power_consumption.txt` in the same folder as the notebook.
3. Run the cells from top to bottom. A CUDA GPU is used automatically if
   available, otherwise it falls back to CPU.
4. If needed, install the required packages using the `requirements.txt`:
   ```bash
   pip install -r requirements.txt
   ```

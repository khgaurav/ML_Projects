# Assignment 03 Practical Questions & Answers

## 1. What are the model's key parameters?

- **Regularization Strength ($\alpha$):** 1.0 (Ridge regression is used to keep the fit stable across many one-hot encoded variables).
- **Intercept:** -206.275 (Note: The target variable $y = \log(1 + \text{Price})$ is log-transformed, which affects the scale of the intercept).

## 2. What are the most significant features according to the coefficients?

Below are the top 15 features by their absolute coefficient values:

| Feature | Coefficient | Influence |
| :--- | :--- | :--- |
| `Model_E-Class E 200 Avantgarde` | 0.8457 | Strong positive effect |
| `Make_Porsche` | 0.7065 | Strong positive effect (luxury brand) |
| `Make_Land Rover` | 0.5712 | Strong positive effect (luxury brand) |
| `Model_Commuter HiAce 3.0 L` | 0.5617 | Strong positive effect |
| `Model_Alto VXI` | -0.4773 | Strong negative effect (budget vehicle) |
| `Model_LX SUV Petrol` | 0.4762 | Strong positive effect |
| `Model_Discovery 3.0 TDV6 HSE` | 0.4596 | Strong positive effect |
| `Model_XF R 5.0 V8 Supercharged` | 0.4563 | Strong positive effect |
| `Make_Maruti Suzuki` | -0.4530 | Strong negative effect (common budget brand) |
| `Make_Honda` | -0.4491 | Moderate negative effect |
| `Make_MINI` | 0.4466 | Strong positive effect |
| `Make_Tata` | -0.4407 | Moderate negative effect |
| `Max Power_570 bhp @ 5250 rpm` | 0.4384 | Positive effect (high horsepower engine) |
| `Make_Rolls-Royce` | 0.4384 | Strong positive effect (luxury brand) |
| `Engine_6592 cc` | 0.4384 | Positive effect (large engine capacity) |

## 3. How accurate are the predictions on unseen test data?

The model was evaluated on a 20% unseen test split with the following performance metrics:

- **$R^2$ Score:** 0.5865 (The model explains approximately 58.7% of the variance in used-car prices).
- **Mean Absolute Error (MAE):** 330,803.66 (On average, predictions deviate from actual prices by about 330,804 INR).
- **Root Mean Squared Error (RMSE):** 1,699,653.96

## 4. How do we interpret the results?

- Numeric columns (like `Year` and `Kilometer`) are kept numeric. Newer cars (higher year) and lower usage (fewer kilometers) lead to higher predicted prices.
- Categorical features are one-hot encoded. Budget brands like Maruti Suzuki or Tata have negative coefficients relative to the reference base, while luxury brands (Porsche, Land Rover, Rolls-Royce) have strong positive coefficients.
- High engine capacity (`Engine`) and horsepower (`Max Power`) also contribute positively to the price.

## 5. What is the predicted price for the new sample listing?

The last cell of the notebook creates a custom vehicle listing with the following attributes:
- **Make/Model:** Honda Amaze 1.2 VX i-VTEC (templated from listing 0)
- **Year:** 2020
- **Kilometer:** 32,000 km
- **Fuel Type:** Diesel
- **Transmission:** Manual
- **Location:** Bangalore
- **Owner:** First Owner
- **Seller Type:** Individual

Using the fitted Ridge model, the predicted fair market price for this vehicle is:
**1,198,885** (in the dataset's currency, INR)

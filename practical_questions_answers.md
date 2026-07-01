# Assignment 02 Practical Questions Answers

## 1. What does the base plan cost before any add-ons?

The base plan costs about £24.97 per month. This is the intercept, so it represents the predicted monthly charge when the model features are at their reference values.

## 2. How much does each individual add-on contribute to the monthly bill?

Each coefficient is the model's estimate of how much that service adds to the monthly charge:

- PhoneService: about £20.04
- MultipleLines: about £5.01
- OnlineSecurity: about £5.05
- OnlineBackup: about £4.98
- DeviceProtection: about £5.01
- TechSupport: about £5.03
- StreamingTV: about £9.98
- StreamingMovies: about £9.95
- InternetService_Fiber optic: about £24.95
- InternetService_No: -£25.05

## 3. Which add-on is the most expensive, and which is the cheapest?

The most expensive positive contributor is InternetService_Fiber optic at about £24.95.

The cheapest coefficient is InternetService_No at about -£25.05. That negative sign means the model predicts a lower monthly charge when the customer is in the no-internet category compared with the reference internet option.

## 4. If a customer adds fiber internet plus both streaming services, how much should their bill rise?

The increase is approximately the sum of those three coefficients:

- Fiber optic: £24.95
- StreamingTV: £9.98
- StreamingMovies: £9.95

Total increase: about £44.88 per month.

## 5. Given a specific bundle, what monthly charge should we expect?

For a customer with phone service, multiple lines, and tech support, the predicted monthly charge is approximately:

- Base plan: £24.97
- PhoneService: £20.04
- MultipleLines: £5.01
- TechSupport: £5.03

Expected monthly charge: about £55.05.

## 6. Is knowing which services a customer has meaningfully better than just knowing how many they have, for predicting the bill?

Yes. The multivariable model is much better than the simple add-on count model.

- Multivariable model: R2 = 0.9988, MAE = 0.7886, RMSE = 1.0504
- Single-variable baseline: R2 = 0.7009, MAE = 14.2369, RMSE = 16.4551

That means knowing the exact services gives much more accurate predictions than just knowing how many add-ons a customer has.

## 7. How accurate are our predictions on unseen customers?

The multivariable model is extremely accurate on the test set. Its MAE is about £0.79 and RMSE is about £1.05.

That means the model is usually off by less than a pound, and even the typical larger errors are still around only £1.

## 8. Do the model's learned prices match Telco's actual price list, and are any coefficients surprising?

Yes, the learned prices broadly match the expected Telco price structure. Fiber optic is the largest add-on, and the streaming services have moderate positive effects.

The most surprising coefficient is InternetService_No, which is negative. It is because the the category is labelled as a negative and having no internet service reduces the bill.

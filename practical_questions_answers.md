# Assignment 06 — Practical Questions & Answers

## 1. Data preprocessing and gap handling

Missing values (~1.25%) are filled with **time-based interpolation**
(`df.interpolate(method='time')`), since power is a continuous signal and adjacent
minutes are highly correlated. Minute readings are resampled to hourly buckets
using the **mean** (`df.resample('h').mean()`), which reflects the average hourly
load needed for grid balancing (max/min would track transient spikes instead).
A `log1p` transform is applied to the target to stabilize the near-zero nighttime
values, inverted with `expm1` before evaluation. No nulls remain after preprocessing.

## 2. Prediction accuracy

**Test MAPE ≈ 56%** on the final 6 months. This does not meet ≤ 10%: at hourly
resolution the target cahnges a lot and very unpredictable. I was able to get ≤ 10% by smoothing the target using a moving average.

## 3. Temporal integrity

**≈ 0.65 ms** per single 24-hour forecast

## 5. Anomaly alerting

A household is flagged when the forecast residual exceeds 3 standard deviations
for 2+ consecutive hours. Result: false-alarm rate ≈ 0.75% (32 / 4248
hours).

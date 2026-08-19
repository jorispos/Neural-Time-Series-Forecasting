# Neural Network Time-Series Forecasting 📈

A 2022 university group project exploring recursive 18-step forecasting across 474 variable-length time series with a multilayer perceptron.

> **Archive note**
>
> This README was refreshed in 2026 to document the project more clearly. The implementation and results remain from the original coursework.

![Observed, held-out, and predicted values for one time series](Plots/predictionplots/Graph207.png)

## 🧠 Approach

The forecasting pipeline combines classical preprocessing with a compact neural network.

1. Hold out the final 18 values of every series for evaluation.
2. Estimate and remove trend and weekly seasonality.
3. Convert the remaining data into rolling 15-step windows.
4. Scale the windows and train a multilayer perceptron with three hidden layers.
5. Predict recursively across the 18-step horizon.
6. Restore the estimated seasonal and trend components before scoring.

## 📊 Original Results

| Evaluation | Result |
| --- | ---: |
| One-step test sMAPE | 24.2 |
| One-step test R² | 0.138 |
| Held-out 18-step sMAPE | 28.6 |

These are the original project's own evaluation outputs. They reflect an educational forecasting experiment, not a validated trading strategy.

## 🛠️ Run Locally

```bash
python -m venv .venv
source .venv/bin/activate
pip install matplotlib numpy scikit-learn statsmodels

cd Program
PYTHONPATH=.. python Main.py
```

The main script trains the model, reports the one-step and held-out scores, and writes the 18-step forecasts to `Data/predictions.csv`.

## 📁 Repository Guide

- `Program/Main.py` runs the full training and forecasting pipeline
- `Program/Henk.py` defines the multilayer perceptron
- `Program/Preprocessing.py` contains trend and seasonality utilities
- `Data/` contains the time-series splits and saved predictions
- `Plots/` contains visualizations from the original experiments

## 👥 Team

Built as a university group project by Joris Postmus, Joris Suurmeijer, Tobias, and Max Kearney.

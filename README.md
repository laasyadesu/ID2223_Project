# ID2223_Project

Solar Energy Prediction Dashboard

This project predicts solar energy generation using historical solar and weather data. It leverages XGBoost for time series regression, incorporating features such as weather conditions.

The workflow includes:

Data processing pipelines to fetch and merge solar and weather data.

Training pipeline for the XGBoost model with a time-based train/test split.

Inference pipeline generating hourly and daily forecasts.

Dashboard displaying predictions: https://laasyadesu.github.io/ID2223_Project/

Hourly predictions for the current day

Daily predictions for the upcoming week

While this project focuses on solar energy, the pipelines and model architecture can be adapted for other energy sources and multiple areas.

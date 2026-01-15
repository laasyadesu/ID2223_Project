# Solar Energy Prediction Dashboard

This project predicts solar energy generation using historical solar and weather data. It leverages **XGBoost** for time series regression, incorporating features such as weather conditions and timestamps. The workflow is built with **Hopsworks Feature Store** for managing, versioning, and serving features efficiently.

---

## Data Sources

- **Svenska Kraftnät** – historical solar energy measurements  
- **Open Meteo / New Weather Data** – meteorological features including:  

  | Feature               | Type       | Notes                     |
  |-----------------------|-----------|---------------------------|
  | `datetime`            | timestamp | Primary key, event time   |
  | `temperature_2m`      | float     | Daily and hourly temperature |
  | `shortwave_radiation` | float     | Solar radiation           |
  | `cloud_cover`         | float     | Cloudiness percentage     |
  | `wind_speed_10m`      | float     | Wind speed                |
  | `precipitation`       | float     | Rainfall                  |
  | ...                   | ...       | Additional features can be added |

---

## Project Structure and Pipelines

### 1. Data Processing Pipelines
- **Notebooks:** `daily_feature.ipynb`, `feature_backfill.ipynb`  
- **Purpose:** Fetch and merge solar and weather data into Hopsworks feature groups  
- **Details:**  
  - Prepares features for training and inference  
  - Handles daily and weekly forecasts
  - Generates cleaned datasets stored in Hopsworks
### 2. Training Pipeline
- **Notebook:** `training_pipeline.ipynb`  
- **Purpose:** Train an XGBoost regression model to predict solar energy generation  
- **Details:**  
  - Reads features from feature view in Hopsworks  
  - Uses time-based train/test split
  - Saves trained model to Hopsworks Model Registry 

### 3. Inference Pipeline
- **Notebook:** `inference_pipeline.ipynb`  
- **Purpose:** Generate hourly and daily predictions for solar energy  
- **Details:**  
  - Reads forecasted weather features from Hopsworks
  - Uses the trained XGBoost model from Model Registry  
  - Produces hourly predictions for the current day  
  - Produces daily predictions for the upcoming week  
  - Saves predictions back to feature groups and generates PNGs for visualization  

### 4. Dashboard
- **Purpose:** Display the solar energy forecasts visually  
- **Location:** [Live Dashboard](https://laasyadesu.github.io/ID2223_Project/)  
- **Details:**  
  - Shows hourly predictions for the current day  
  - Shows daily predictions for the upcoming week  
  - Can be automatically updated via GitHub Actions  

---

## Extensibility

While this project focuses on solar energy, the pipelines and model architecture can be adapted for:

- Other renewable energy sources
- Multiple geographic areas  
- Additional weather features or external datasets  

---

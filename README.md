## Project Overview

This project develops an end-to-end machine learning pipeline to forecast hourly traffic volume across NYC roadway segments using IoT sensor data.

The system combines:
- Exploratory data analysis (EDA)
- Unsupervised learning (K-Means clustering, anomaly detection)
- Supervised learning (Elastic Net regression)
- Feature engineering for time-series data

The goal is to enable data-driven traffic forecasting and smarter urban planning decisions.

## Key Results

- Final model: Elastic Net Regression
- Test R²: ~0.78
- RMSE: ~124 vehicles/hour
- MAE: ~84 vehicles/hour

The model captures ~78% of traffic variance using only temporal and location-based features.

## Modeling Pipeline

1. Data Cleaning & Reshaping (wide → long format)
2. Feature Engineering:
   - Cyclical encoding (sin/cos for time)
   - Lag features (1 hour, 1 day, 1 week)
   - Weekend indicator
3. Unsupervised Learning:
   - K-Means clustering of traffic patterns
   - Z-score anomaly detection
4. Supervised Learning:
   - Baseline Linear Regression
   - Elastic Net (final model)
5. Evaluation:
   - Time-series cross-validation
   - Holdout test set

## Repository Structure

data/
  raw/                # input datasets (not included in repo)
  README.md

docs/
  clustering_summary.docx

notebooks/
  01_data_preparation_and_eda.ipynb
  02_final_eda.ipynb
  03_kmeans_clustering_analysis.ipynb
  04_baseline_linear_model.ipynb
  05_baseline_linear_model_2.ipynb
  06_elastic_net_model.ipynb

presentations/
  final_presentation.pptx

reports/
  final_report.pdf

README.md
requirements.txt

## How to Run

1. Install dependencies:
   pip install -r requirements.txt

2. Place dataset in:
   data/raw/

3. Run notebooks in order:
   notebooks/01 → notebooks/06

## Business Value

- Enables proactive traffic congestion management
- Identifies high-risk roadway segments
- Supports infrastructure planning and resource allocation
- Detects anomalies such as accidents or disruptions

## Data Source

This project uses the NYC Open Data Traffic Volume Counts dataset:

https://data.cityofnewyork.us/Transportation/Traffic-Volume-Counts-Historical-/btm5-ppia/about_data

Due to GitHub file size limitations, raw datasets are not included in this repository.

### Dataset Overview
- ~1M+ observations after transformation
- Hourly traffic volume across NYC roadway segments
- Includes temporal and location-based features

### Local Files Used
- `01_Traffic_Volume_Counts_preprocessed.csv`
- `02_structured_traffic.csv`

To reproduce results, download the dataset from the source above and place it in:

`data/raw/`

### Note on PySpark
This project uses PySpark. If running locally, ensure:
- Java is installed
- Apache Spark is configured
- OR run in Databricks
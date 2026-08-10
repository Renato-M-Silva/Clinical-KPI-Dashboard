# Clinical KPI Dashboard

A data analysis project focused on clinical performance indicators, patient outcomes, and rehabilitation efficiency. Built using Python, Pandas, SQL, and Power BI, this dashboard transforms raw clinical data into actionable insights for healthcare decision-making.

## Project Overview

This project simulates a real-world healthcare analytics workflow, including:

- Clinical data ingestion
- Data cleaning and validation
- KPI creation (pain reduction, mobility gain, recovery time, success rate)
- Exploratory data analysis
- Dashboard development in Power BI
- Data storytelling for clinical decision support

The goal is to demonstrate how a Healthcare Data Analyst can convert patient data into meaningful insights for clinicians, administrators, and rehabilitation teams.

## Dashboard Features

### 1. Clinical Overview
- Average recovery time
- Rehabilitation success rate
- Average number of sessions
- Mean pain reduction
- Mean mobility gain

### 2. Injury Type Analysis
- Recovery time by injury type
- Success rate by injury type
- Pain improvement distribution
- Mobility gain comparison

### 3. Patient Evolution
- Pain score progression
- Mobility progression
- Individual patient outcome trends

### 4. Sessions Efficiency
- Relationship between number of sessions and recovery time
- Efficiency indicators
- Outlier detection

## Dataset Description

The dataset is a synthetic clinical dataset created for educational and portfolio purposes. It contains anonymized, simulated patient rehabilitation data with the following fields:

| Column | Description |
|--------|-------------|
| patient_id | Unique patient identifier |
| age | Patient age |
| gender | M/F |
| injury_type | Type of injury (muscle, joint, ligament, etc.) |
| start_date | Rehabilitation start date |
| end_date | Rehabilitation end date |
| sessions | Number of therapy sessions |
| pain_score_initial | Initial pain score (0–10) |
| pain_score_final | Final pain score (0–10) |
| mobility_initial | Initial mobility score (0–100) |
| mobility_final | Final mobility score (0–100) |

## Data Processing (Python)

The project includes a Python ETL pipeline that performs:

- Duplicate removal
- Date conversion
- KPI calculations
- Success flag creation
- Export of cleaned dataset

Example code snippet:

```python
import pandas as pd

df = pd.read_csv("clinical_data.csv")

df = df.drop_duplicates()

df["start_date"] = pd.to_datetime(df["start_date"])
df["end_date"] = pd.to_datetime(df["end_date"])

df["recovery_days"] = (df["end_date"] - df["start_date"]).dt.days
df["pain_improvement"] = df["pain_score_initial"] - df["pain_score_final"]
df["mobility_gain"] = df["mobility_final"] - df["mobility_initial"]

df["success"] = (df["mobility_gain"] > 20) & (df["pain_improvement"] > 2)

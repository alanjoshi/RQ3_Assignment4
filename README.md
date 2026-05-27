# RQ3 Assignment 4 - NSW Road Crash Severity Classification

This repository contains the code, dataset access information, and output files for Research Question 3 of the PRT564 Group Project.

## Research Question

Can crash severity be anticipated using variables like time interval, location type, and the number of traffic units involved?

## Project Overview

This project uses NSW road crash data enriched with Transport for NSW traffic-volume data to classify crash severity. The classification target is `casualty_crash`, where fatal and injury crashes are grouped as casualty crashes, and non-casualty towaway crashes are grouped as non-casualty crashes.

The analysis compares three classification models:

- Naive Bayes
- Decision Tree
- Random Forest

The Random Forest model was also tuned using grid search cross-validation.

## Repository Structure


notebooks/
  Build_NSW_Crash_Traffic_Enriched_Dataset.ipynb
  RQ3_Assignment4_Crash_Severity_Classification.ipynb

outputs/
  rq3_model_test_results.csv
  rq3_cross_validation_results.csv
  rq3_final_model_results.csv
  rq3_feature_importance.csv
  rq3_target_distribution.csv
  rq3_degree_of_crash_distribution.csv
  rq3_location_type_summary.csv
  rq3_time_interval_summary.csv
  rq3_traffic_units_summary.csv
## Data Sources

The analysis uses the following datasets:

1. NSW Road Crash Data 2020-2024  
   Used as the main crash dataset for the group project.  
   Source: https://www.data.gov.au/data/dataset/nsw-2-nsw-crash-data

2. NSW Roads Traffic Volume Counts API - Station Reference  
   Used to obtain traffic count station details such as road name, LGA, suburb, coordinates, road classification, and station information.  
   Source: https://opendata.transport.nsw.gov.au/dataset/nsw-roads-traffic-volume-counts-api

3. NSW Roads Traffic Volume Counts API - Yearly Summary  
   Used to obtain yearly traffic-volume variables such as all-day traffic counts, weekday/weekend traffic, AM/PM peak traffic, and heavy vehicle counts.  
   Source: https://opendata.transport.nsw.gov.au/dataset/nsw-roads-traffic-volume-counts-api

Large source datasets are not included in this repository. They should be downloaded separately from the links above.
The main analysis-ready dataset is too large to store directly in this repository. It can be accessed from the OneDrive link below:
https://charlesdarwinuni-my.sharepoint.com/:x:/g/personal/s395095_students_cdu_edu_au/IQBBPjWFk4B8T5W7ljgkeLsMAXdCmR8LXHZxljYQyi5IKuM?e=aoSTbA
This dataset was created by combining the preprocessed NSW crash dataset with Transport for NSW traffic volume datasets.
## Dataset Preparation

The enriched dataset was created by joining the preprocessed NSW crash dataset with traffic-volume station reference data and yearly traffic summary data.

The added traffic-volume variables include:

- matched traffic station details
- traffic volume counts
- heavy vehicle volume
- heavy vehicle share
- road hierarchy
- road classification
- lane count
- traffic match quality

## Classification Target

The classification target used in this project is `casualty_crash`.

The target was created from the `Degree of crash` column:

- `0`: Non-casualty towaway crash
- `1`: Casualty crash, including fatal and injury crashes

This binary target was used because fatal crashes were much less common than injury and non-casualty crashes.

## Feature Engineering

The notebook creates several engineered features for modelling:

- `is_peak_time`
- `is_late_night`
- `is_intersection`
- `is_high_speed`
- `traffic_units_group`
- `log_all_vehicles_all_days`
- `heavy_vehicle_share_available`

These features were created to better represent the time interval, location type, traffic-unit involvement, speed environment, and traffic-volume context.

## Models Used

The following classification models were developed and compared:

- Naive Bayes
- Decision Tree Classifier
- Random Forest Classifier
- Tuned Random Forest Classifier

The Random Forest model was tuned using `GridSearchCV`.

## Model Evaluation

The models were evaluated using:

- Accuracy
- Precision
- Recall
- F1-score
- ROC-AUC
- Confusion matrix
- ROC curve
- Five-fold cross-validation

## Main Findings

Naive Bayes achieved the strongest recall and F1-score, making it useful for identifying casualty crashes. Tuned Random Forest achieved the highest ROC-AUC and provided feature importance results.

The most important predictors included:

- traffic volume
- speed limit
- month
- day
- natural lighting
- number of traffic units involved
- heavy vehicle share

Overall, the results show that crash severity can be partly anticipated using time interval, location type, number of traffic units involved, and enriched traffic-volume variables. However, the model performance was moderate, suggesting that additional variables such as driver behaviour, actual speed, alcohol or drug involvement, seatbelt use, and vehicle condition may improve future prediction.

## Output Files

The `outputs/` folder contains the generated result files:

- `rq3_model_test_results.csv`
- `rq3_cross_validation_results.csv`
- `rq3_final_model_results.csv`
- `rq3_feature_importance.csv`
- `rq3_target_distribution.csv`
- `rq3_degree_of_crash_distribution.csv`
- `rq3_location_type_summary.csv`
- `rq3_time_interval_summary.csv`
- `rq3_traffic_units_summary.csv`

## Notes

Large source datasets are not stored directly in this repository. The analysis-ready dataset is provided through the OneDrive link above.

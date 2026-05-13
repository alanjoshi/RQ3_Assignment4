# RQ4 Assignment 4 - NSW Road Crash Classification

This repository contains the code and output files for Research Question 4 of the PRT564 Group Project.

## Research Question

Can high-injury crashes be classified using traffic-unit involvement and enriched traffic-volume variables?

## Files

- `Build_NSW_Crash_Traffic_Enriched_Dataset.ipynb`  
  Builds the enriched dataset by combining the preprocessed NSW crash dataset with Transport for NSW traffic-volume data.

- `RQ4_Assignment4_Classification_Analysis.ipynb`  
  Performs exploratory data analysis, creates the classification target, trains baseline and enriched models, evaluates performance, and exports result tables.

- `rq4_model_test_results.csv`  
  Final model performance on the test set.

- `rq4_cross_validation_results.csv`  
  Five-fold cross-validation results.

- `rq4_feature_importance.csv`  
  Feature importance from the tuned enriched decision tree.

- `rq4_target_distribution.csv`  
  Distribution of low/no injury and high-injury crashes.

- `rq4_traffic_units_summary.csv`  
  High-injury rate by number of traffic units involved.

- `rq4_traffic_volume_summary.csv`  
  High-injury rate by traffic-volume band.

- `nsw_crash_traffic_volume_analysis_ready.csv`
  This CSV is used by `RQ4_Assignment4_Classification_Analysis.ipynb`.

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


## Methods

The classification target was defined as:

- `0`: low/no injury crash, where `Total_casualties` is 0 or 1
- `1`: high-injury crash, where `Total_casualties` is 2 or more

Models used:

- Logistic Regression
- Decision Tree Classifier

Model evaluation used:

- Accuracy
- Precision
- Recall
- F1-score
- ROC-AUC
- Confusion matrix
- Five-fold cross-validation

## Main Finding

The number of traffic units involved was the strongest predictor of high-injury crashes. Traffic-volume enrichment added useful contextual information, with `all_vehicles_all_days` appearing among the important predictors, but it did not substantially improve overall predictive performance compared with the baseline model.

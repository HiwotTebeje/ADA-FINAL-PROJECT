# ADA Final Project: NHANES Data Analysis

## Project Description
This repository includes the R Markdown file used to analyze NHANES 2021–2023 data for the Advanced Data Analysis final project.
The purpose of this study is to evaluate the association between depression (PHQ-9 ≥10) and obesity (BMI ≥30) among U.S. adults.
The analysis uses:
- Complex survey weights
- Multiple imputation
- Survey-weighted regression models
- Effect modification testing
- Diagnostic evaluation
All analyses were conducted using R Markdown.

## Files Included
- ADA Final Project.Rmd: R Markdown file used to clean, analyze, and model the NHANES data
- README.md: This file

## What the Code Does

#Chunk 1 – Setup

Sets global knitr options to control how output is displayed.

#Chunk 2 – Install packages

Installs R packages required for analysis (only needed the first time).

#Chunk 3 – Load packages

Loads all packages used for importing data, survey analysis, imputation, regression, and visualization.

#Chunk 4 – Read the Data

Imports NHANES 2021–2023 SPSS files into R.

#Chunk 5 – Define Analytic Sample

Filters the NHANES data to include:
- Adults (≥18 years)
- Non-pregnant individuals
Then defines depression and obesity variables.

#Chunk 6 – Create PHQ-9 and Binary Variables

- Computes PHQ-9 total score
- Creates:
- Depression variable (PHQ-9 ≥10 vs <10)
- Obesity variable (BMI ≥30 vs <30)

#Chunk 7 – Examine Missingness

Computes missing number and percentage for key variables.
Sleep duration was the only variable with missing values.

#Chunk 8 – Prepare Variables for Imputation

Creates a reduced data frame containing variables selected for imputation and modeling.

#Chunk 9 – Build Final Analytic Dataset

Produces the analytic dataset with renamed variables and keeps only needed data fields.

#Chunk 10 – Missingness Pattern

Displays missingness combinations using md.pattern() to evaluate joint missingness.

#Chunk 11 – Visual Missingness Exploration

Uses plotting to visually compare distributions of missing vs. observed values.

#Chunk 12 – Boxplots

Creates visual comparisons of variables (example: sleep duration vs. depression status).

#Chunk 13 – Multiple Imputation

Uses mice() to impute missing values:
- Runs predictive mean matching
- Creates 5 imputed datasets (m = 5)

#Chunk 14 – Inspect Imputed Values

Identifies which variables were imputed and checks imputed values for:
- Sleep duration
- BMI
- PHQ-9

#Chunk 15 – Extract Completed Dataset

Selects one completed dataset for diagnostics and exploratory checks.

#Chunk 16 – Main Regression Model (Survey Weighted)

Fits survey-weighted logistic regression:
- Outcome: obesity
- Exposure: depression
- Adjusted for age, sex, and sleep duration
Generates adjusted odds ratios and 95% CIs.

#Chunk 17 – Model Diagnostics

Evaluates model reliability using:
- Hosmer–Lemeshow test
- Residual plots
- Cook’s distance
- Multicollinearity (VIF)

#Chunk 18 – Effect Modification (Sex × Depression)

Tests whether the relationship between depression and obesity differs by sex using an interaction term.

#Chunk 19 – Sensitivity Analysis (Complete Case)

Repeats the analysis using only complete data (no imputation) and compares results to the imputed model.

#Chunk 20 – Flow Diagram

Displays a flowchart summarizing:
- Initial sample
- Exclusion criteria
- Final analytic sample size
- Variables handled by imputation

#Chunk 21 – Descriptive Table

Generates weighted descriptive statistics for:
- Age
- Sleep duration
- BMI
- Sex
Compared between individuals with and without depression.

#Chunk 22 – Export Regression Tables

Formats model results into publication-ready tables and exports them to CSV files.

## Author
Name: Hiwot Tebeje
Course: Advanced Data Analysis (ADA)
Date: December 2025


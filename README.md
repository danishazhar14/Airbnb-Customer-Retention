# Airbnb Customer Retention Strategy
This repository contains the code and analysis for designing a customer retention strategy for Airbnb properties. The project is part of the MGMT 52610 Data- and AI-Driven Marketing course (Fall 2024) and aims to optimize Airbnb’s net profit by selectively retaining properties through a $1000 gift incentive.

## Project Overview
In the competitive landscape of customer relationship management (CRM), retaining existing customers is often much more cost-effective than acquiring new ones. For Airbnb, hosts (property owners) sometimes choose to delist their properties from the platform, leading to attrition. This project uses historical data to predict host attrition and recommends a targeted retention strategy.

## Key Objectives:
Predict Host Attrition: Utilize historical property data (from abb.csv) to model the likelihood of a host removing their property from Airbnb. Develop a Retention Strategy: Determine which properties should receive a $1000 gift to incentivize continued listing. The retention decision is based on predicted attrition probabilities and margin contributions. Maximize Net Profit: Calculate net profit as 15% of the total revenue from properties that remain, minus the cost of retention efforts.

## Data Description
The analysis uses two main datasets:

- abb.csv: Historical dataset containing: Property information (ID, location, number of bedrooms and bathrooms, average daily rate) Reservation days for each of the past 12 months (reservationdays1 - reservationdays12) Various property ratings (overall, communication, accuracy, cleanliness, check-in, location, value) Attrition outcome (whether the host delisted the property)

- abb_new.csv: Current dataset of Airbnb properties for which the retention strategy needs to be applied. For further details, refer to the project document: hw5 - Airbnb retention.pdf.

## Methodology
1. Exploratory Data Analysis (EDA)
Data Inspection: Verify data quality and absence of null values. Visualization: Generate box plots and pair plots to understand feature distributions and identify outliers.

2. Data Cleaning and Feature Engineering
New Features:
Booking Growth: Calculated as the Compound Annual Growth Rate (CAGR) of reservation days. Past 6-Month Ratio: Ratio of the sum of reservation days in the latter half of the year to the total annual reservation days. Total Reservations & Annual Revenue: Computed from the daily rate and reservation days.

- Preprocessing Pipeline:
Extreme Imputer: Caps feature values outside three standard deviations to reduce the impact of outliers. Standard Scaling: Normalizes selected features for improved model performance.

3. Modeling and Validation
Variable Selection: Lasso regression is used to evaluate variable importance and visualize the effect of different regularization strengths. Ensemble Modeling: A stacking classifier combining Random Forest, MLP, and Gradient Boosting models is trained to predict host attrition. Performance Metrics: Model performance is evaluated using ROC curves, confusion matrices, and classification reports. ROI Analysis: Simulations determine the optimal probability cutoffs for gift allocation to maximize net profit. The analysis segments properties by margin quantiles for a more tailored strategy.

4. Final Prediction
Test Data Processing: The same feature engineering and preprocessing steps are applied to the test data (abb_new.csv). Retention Decision: A final retention strategy is developed by assigning a gift (1 for retention, 0 for no gift) based on predicted probabilities and segment-specific optimal cutoffs. Output: The final recommendations are saved to submission.csv.

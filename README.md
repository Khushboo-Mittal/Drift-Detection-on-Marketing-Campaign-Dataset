# Drift Detection on Marketing Campaign Dataset

## Overview

This project aims to detect data drift in a marketing campaign dataset by comparing historical and current/future data samples. Data drift occurs when the distribution of data changes over time, potentially impacting model performance. Drift detection helps ensure the reliability of predictive models by identifying shifts in data distribution.

The project focuses on:

- Numerical data drift using the **Kolmogorov-Smirnov test**.
- Categorical data drift using the **Chi-square test**.
- Simulating significant drift to test the framework’s efficacy.

---

## Project Structure

### Files

- **`marketing_campaign.csv`**: Input dataset containing customer details and campaign responses.
- **`DriftDetection.ipynb`**: Jupyter notebook containing the code for processing the data and performing drift detection.
- **`README.md`**: Documentation file describing the project.

### Key Libraries

- **Pandas**: For data manipulation and analysis.
- **NumPy**: For numerical operations.
- **Matplotlib**: For data visualization.
- **SciPy**: For statistical tests.

---

## Dataset Details

### Features

The dataset includes the following columns:

- **ID**: Unique identifier for each customer.
- **Year_Birth**: Birth year of the customer.
- **Education**: Education level of the customer.
- **Marital_Status**: Marital status of the customer.
- **Income**: Yearly income of the customer.
- **Kidhome/Teenhome**: Number of kids and teenagers at home.
- **Dt_Customer**: Date of customer enrollment.
- **Recency**: Days since last purchase.
- **MntWines**, **MntFruits**, etc.: Amount spent on various products.
- **NumWebVisitsMonth**: Number of website visits in the last month.
- **Response**: Response to the campaign.

---

## Steps for Drift Detection

### 1. Preprocessing

- Load the dataset using Pandas.
- Remove infrequent categories in categorical columns (e.g., `Marital_Status`).

### 2. Sampling

- Split the dataset into two samples:
  - **`data_1`**: Historical data.
  - **`data_2`**: Current data.

### 3. Drift Detection Tests

#### Kolmogorov-Smirnov Test for Numerical Columns

- **Purpose**: Detect differences in numerical data distributions.
- **Significance Level**: 5% (p-value = 0.05).
- **Results**:
  - No drift detected in the initial comparison.
  - Drift detected in modified future data (“Income”, “Recency”, “MntWines”).

#### Chi-square Test for Categorical Columns

- **Purpose**: Detect differences in categorical data distributions.
- **Significance Level**: 5% (p-value = 0.05).
- **Results**:
  - No drift detected initially.
  - Drift detected in modified future data (“Marital_Status”).

### 4. Drift Simulation

- Introduced significant changes to the “Income”, “Recency”, and “MntWines” columns.
- Simulated changes in “Marital_Status” to increase the “Married” population.

### 5. Visualization

- Histograms for numerical columns before and after drift simulation.
- Bar charts for categorical column distributions.

---

## Output Summary

### Initial Comparison

- **Numerical Drift**: No drift detected.
- **Categorical Drift**: No drift detected.

### Post Drift Simulation

- **Numerical Drift**:
  - Detected in “Income”, “Recency”, and “MntWines”.
- **Categorical Drift**:
  - Detected in “Marital_Status”.

---

## Usage Instructions

### Prerequisites

- Install required libraries: `pip install numpy pandas matplotlib scipy`.

### Running the Code

1. Place `marketing_campaign.csv` in the same directory as the notebook.
2. Open and run `DriftDetection.ipynb` in Jupyter Notebook or any compatible IDE.
3. Visualize results through the generated plots and notebook outputs.

---

## Conclusion

This project demonstrates an effective approach to identifying data drift in both numerical and categorical features, helping maintain the reliability of predictive models in dynamic environments.

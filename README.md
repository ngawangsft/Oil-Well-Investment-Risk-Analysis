# Oil Well Profit Prediction — OilyGiant

## Overview
OilyGiant mining company needs to select the most profitable region to develop a new oil well. Using geological survey data from three regions, I built linear regression models to predict oil reserve volumes and applied bootstrapping to evaluate potential profit and risk. The goal is to identify the region that maximizes profit while keeping the risk of losses below 2.5%.

## Business Problem
Choosing the wrong location for drilling can lead to significant financial losses. By leveraging data on oil well parameters, the company can:
- Estimate the volume of reserves in potential new wells
- Select the 200 most promising wells per region based on predictions
- Calculate expected profit and assess risk using bootstrapping
- Make a data‑driven decision that minimizes risk and maximizes return

**Objective** Recommend the region with the highest average profit and a loss probability below 2.5%, based on 1,000 bootstrap samples.

## Highlights & Key Results
- Built linear regression models for three regions (only algorithm allowed by business conditions)
- Evaluated models using RMSE and average predicted reserves
- Calculated break‑even volume (111 thousand barrels per well) and compared with regional averages
- Selected top 200 wells per region based on predictions to estimate profit
- Applied bootstrapping (1,000 samples) to determine profit distribution, confidence intervals, and loss risk

### Model Performance & Profit Analysis

| Region | RMSE | Avg. Predicted Reserves (k bbl) | Avg. Profit (bootstrapped) | 95% CI (million USD) | Loss Risk |
|--------|------|----------------------------------|----------------------------|------------------------|-----------|
| 0      | 37.58 | 92.08                           | 6.80 M                     | [5.2, 8.4]             | 7.2%      |
| 1      | 0.89  | 68.69                           | 7.78 M                     | [6.9, 8.7]             | **1.5%**  |
| 2      | 40.03 | 94.77                           | 4.42 M                     | [2.0, 6.8]             | 6.8%      |

## Final Region Selection
**Region 1** was selected as the optimal location because:
- It is the only region with a loss risk below the 2.5% threshold (1.5%)
- It yields the highest average profit (~7.78 million USD)
- The model for Region 1 is extremely accurate (RMSE = 0.89), indicating reliable predictions
- Despite having lower average predicted reserves, the selected top wells generate strong profits with minimal variability

## Tools & Technologies
Python, pandas, NumPy, scikit‑learn (Linear Regression), Matplotlib, Jupyter Notebook

## Dataset
The geological exploration data for the three regions can be downloaded directly from the following URLs:

- [geo_data_0.csv](https://practicum-content.s3.us-west-1.amazonaws.com/datasets/geo_data_0.csv)
- [geo_data_1.csv](https://practicum-content.s3.us-west-1.amazonaws.com/datasets/geo_data_1.csv)
- [geo_data_2.csv](https://practicum-content.s3.us-west-1.amazonaws.com/datasets/geo_data_2.csv)

The notebook loads the data directly from these URLs using `pd.read_csv()`.

## How to Run
1. Clone or download the repository.
2. Open `oil_well_profit.ipynb` in Jupyter Notebook or VS Code.
3. Run the cells to replicate the analysis and model results. (No need to manually download the datasets – they are loaded directly from the URLs.)

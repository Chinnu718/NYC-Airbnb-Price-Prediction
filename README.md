# Predict New York City Airbnb Prices - Linear Regression

Unlox AIML - Minor Project 2  
**Student:** Chinmaya SD (USN 1AM25CI033)

A Linear Regression model that predicts the nightly price of a New York City Airbnb listing, built and
evaluated step by step in one Jupyter notebook.

## Dataset
*New York City Airbnb Open Data* (AB_NYC_2019), 48,895 listings, originally published on Kaggle.
The dataset file is not included in this repository. The notebook downloads it automatically from
https://github.com/YueminLi/Airbnb_NYC_2019 if `AB_NYC_2019.csv` is not in the same folder.

## How to run
```bash
pip install -r requirements.txt
jupyter notebook ChinmayaSD_NYC_Airbnb_Linear_Regression.ipynb
```
Or open the notebook in Google Colab and choose Runtime > Run all. The notebook already contains all outputs and charts,
so it can also be read directly on GitHub.

## Notebook structure
1. EDA and data auditing (shape, data types, variable types, missing values)
2. Cleaning: drop `last_review`, fill `reviews_per_month` with 0, drop ID and name columns
3. Outliers: boxplots/histograms, remove $0 prices, trim `price` and `minimum_nights` at the 95th percentile
4. Feature selection and encoding: drop high-cardinality `neighbourhood`, one-hot encode borough and room type (`drop_first=True`)
5. Features/target split and 80/20 train-test split (`random_state=42`)
6. Training and evaluation (R-squared, MAE, MSE, RMSE)
7. Residual analysis: actual vs predicted, residual plots, error by price band

## Results (test set, 9,150 listings)
| Metric | Value |
|---|---|
| R-squared | 0.49 |
| MAE | about $38 per night |
| RMSE | about $53 per night |

The model is reasonable for typical listings up to about $250 a night but under-predicts premium listings
(average error about $128 for listings priced $251-$355). The one-page plain-English summary is submitted separately as a PDF.

# Instructions for Running and Testing the Program

Setup Instructions
1. Clone the Repository - https://github.com/albertlee64/MSDS451_Financial_Engineering_Assignment_1.git
2. Create Virtual Environment (Optional but Recommended)
3. Install Required Packages
4. Run in Jupyter Notebook - Assignment_1.ipynb
   

# MSDS451 Financial Engineering Assignment 1

This project builds a machine learning pipeline to predict the 5-day direction (up/down) of Booz Allen Hamilton (BAH) stock using technical indicators and price-derived features. It leverages XGBoost for classification, includes extensive feature engineering, time series cross-validation, and backtesting with return comparisons against a Buy & Hold strategy.

The dataset is based on Polygon.io API. EDA for Booz Allen Hamilton (BAH) stock.

<img width="1390" height="790" alt="image" src="https://github.com/user-attachments/assets/f11d169c-7d2b-47a9-b18a-8e8ca36d6ae5" />


# Project Highlights

Predicts whether BAH will go up or down over the next 5 trading days

Applies feature engineering from technical indicators (RSI, MACD, Bollinger Bands, etc.)

Performs filter-based feature selection (variance & correlation thresholding)

Uses XGBoost with RandomizedSearchCV hyperparameter tuning

Includes confusion matrix, ROC curve, and Sharpe Ratio analysis

Backtests model performance vs. Buy & Hold using cumulative return charts

# Feature Enginerring & Selection
Features are created based on historical price movements:

ret_1m: 1-month return

vol_1m: 1-month volatility (std dev)

momentum_3m: 3-month momentum

price_to_high_1y: Price relative to 1-year high

drawdown_1y: % drop from max price

rsi14: 14-day Relative Strength Index

macd: MACD signal difference

bb_pct: % position in Bollinger Band range

Two-step filtering approach:

Variance Threshold: Remove near-constant features

Correlation Filtering: Drop features with >95% pairwise correlation

<img width="747" height="590" alt="image" src="https://github.com/user-attachments/assets/7cd179be-6b49-4d2d-b185-832e0c3544b8" />

# Model

XGBoostClassifier

Balanced using scale_pos_weight

Tuned using RandomizedSearchCV and TimeSeriesSplit

Evaluated on:

Accuracy, Precision, Recall, F1

Confusion Matrix

ROC-AUC

Sharpe Ratio

Cumulative Return Chart

# Performance Summary

Test Accuracy: ~75%

ROC AUC: ~0.88

Sharpe Ratio (Model Strategy): 2.56

Sharpe Ratio (Buy & Hold): –1.47

Model strategy consistently outperformed Buy & Hold during evaluation period.

<img width="990" height="490" alt="image" src="https://github.com/user-attachments/assets/35a74481-89f8-4af3-b2d9-49e468d8fac3" />

# AI Usage

AI was used to help develop some of the code around RSI candlestick chart as I was not familiar with that Python library package. AI was also used to help refine and perform hyperparameter tuning to improve the accuracy score of the model. The last part was AI was then used to help compare the Model Strategy vs Buy and Hold strategy to ensure the returns were being calculated correctly.

# License

MIT License



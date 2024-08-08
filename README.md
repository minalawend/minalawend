import yfinance as yf
import pandas as pd
import numpy as np

# Fetch historical data for EGX30 from Yahoo Finance
# Replace 'EGX30' with the correct ticker symbol for EGX30 on Yahoo Finance
ticker = '^EGX30'
data = yf.download(ticker, start='2020-01-01', end='2023-12-31')

# Display the first few rows of the data
print(data.head())

# Calculate basic statistical measures
mean = data['Close'].mean()
median = data['Close'].median()
std_dev = data['Close'].std()
variance = data['Close'].var()
min_value = data['Close'].min()
max_value = data['Close'].max()
percentile_25 = np.percentile(data['Close'], 25)
percentile_75 = np.percentile(data['Close'], 75)
skewness = data['Close'].skew()
kurtosis = data['Close'].kurt()

# Display the calculated statistics
print(f"Mean: {mean}")
print(f"Median: {median}")
print(f"Standard Deviation: {std_dev}")
print(f"Variance: {variance}")
print(f"Minimum: {min_value}")
print(f"Maximum: {max_value}")
print(f"25th Percentile: {percentile_25}")
print(f"75th Percentile: {percentile_75}")
print(f"Skewness: {skewness}")
print(f"Kurtosis: {kurtosis}")

# Additional measures
daily_returns = data['Close'].pct_change()
annual_return = daily_returns.mean() * 252
annual_volatility = daily_returns.std() * np.sqrt(252)
sharpe_ratio = annual_return / annual_volatility

print(f"Annual Return: {annual_return}")
print(f"Annual Volatility: {annual_volatility}")
print(f"Sharpe Ratio: {sharpe_ratio}")

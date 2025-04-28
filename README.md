# Financial Data Analysis with Python

This repository demonstrates practical applications of Python for financial data analysis, focusing on stock market data processing and basic analytical techniques.

## Overview

This project showcases Python's capabilities in financial data analysis through:

- Retrieving stock market data from Yahoo Finance
- Processing OHLC (Open, High, Low, Close) price information
- Performing financial calculations and conditional analysis
- Manipulating dates and time series data
- Implementing data formatting techniques

## Requirements

```
yfinance
pandas
numpy
```

Install dependencies with:

```bash
pip install yfinance pandas numpy
```

## Key Features

### Stock Data Acquisition

```python
import yfinance as yf

# Download stock data with flexible time periods
# Options: d (day), wk (week), mo (month), y (year), ytd (year to date), max (all available)
apple_data = yf.download('AAPL', period='5d')
```

### Data Processing

```python
# Quick data overview
print(apple_data.shape)  # Check dimensions
print(apple_data.head())  # Preview content

# Extract the most recent trading day data
last_day_data = apple_data.iloc[-1]

# Access specific price components
open_price = float(last_day_data['Open'])
close_price = float(last_day_data['Close'])
high_price = float(last_day_data['High'])
low_price = float(last_day_data['Low'])
volume = int(last_day_data['Volume'])
```

### Financial Analysis

```python
# Calculate price movement
price_diff = open_price - close_price

# Determine price direction
price_up = close_price > open_price

# Implement threshold checks
is_price_above_150 = close_price > 150

# Conditional logic
threshold_reason = None
if close_price < 150:
    threshold_reason = "Price below threshold"
```

### Date Handling

```python
# Extract the last trading date
last_trading_date = apple_data.index[-1]
last_trading_date_str = last_trading_date.strftime("%Y-%m-%d")

# Date string manipulation
first_character = last_trading_date_str[0]  # First character
last_character = last_trading_date_str[-1]  # Last character
month = last_trading_date_str[5:7]  # Extract month

# Date-based conditions
is_december = month == '12'
```

### Data Presentation

```python
# Format decimal places for consistency
formatted_open_price = f"{open_price:.6f}"

# Display results
print(f"Open: {formatted_open_price}")
print(f"Close: {formatted_close_price}")
print(f"Price difference: {price_diff}")
print(f"Price went up: {price_up}")
print(f"Last trading day: {last_trading_date_str}")
```

## Future Development

- Add data visualization capabilities
- Implement technical indicators (Moving Averages, RSI, MACD)
- Build portfolio analysis tools
- Create automated trading strategy testing
- Develop market sentiment analysis

## License

[MIT License](LICENSE)

---

Feel free to contribute to this project by submitting pull requests or opening issues for suggestions and improvements.

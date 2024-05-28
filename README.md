# AAPL Stock Price Analysis

This repository contains a Python project for downloading, analyzing, and visualizing historical stock price data for Apple Inc. (AAPL) from Yahoo Finance. The project leverages libraries such as yfinance, pandas, and plotly to handle date ranges, fetch financial data, and prepare it for further analysis and visualization.

## Table of Contents
- [Overview](#overview)
- [Installation](#installation)
- [Usage](#usage)

## Overview
This project aims to:
1. Download historical stock price data for Apple Inc. (AAPL) over the past 5000 days.
2. Organize and clean the data for analysis.
3. Provide a framework for visualizing stock price data using candlestick charts and other plots.

## Installation
1. Clone the repository:
    ```bash
    git clone https://github.com/your-username/AAPL-Stock-Price-Analysis.git
    cd AAPL-Stock-Price-Analysis
    ```
2. Create and activate a virtual environment (optional but recommended):
    ```bash
    python3 -m venv venv
    source venv/bin/activate  # On Windows use `venv\Scripts\activate`
    ```
3. Install the required packages:
    ```bash
    pip install -r requirements.txt
    ```

## Usage
1. Ensure you have an internet connection to download data from Yahoo Finance.
2. Update the `data.csv` path in the notebook or script if necessary.
3. Run the Jupyter Notebook or Python script to download, clean, and visualize the data.

### Example
```python
import pandas as pd
import yfinance as yf
import datetime
from datetime import date, timedelta

# Get today's date
today = date.today()

# Calculate the start and end dates for the past 5000 days
end_date = today.strftime("%Y-%m-%d")
start_date = (today - timedelta(days=5000)).strftime("%Y-%m-%d")

# Download stock data
data = yf.download('AAPL', start=start_date, end=end_date, progress=False)

# Prepare the data
data["Date"] = data.index
data = data[["Date", "Open", "High", "Low", "Close", "Adj Close", "Volume"]]
data.reset_index(drop=True, inplace=True)

# Display the first few rows of the data
print(data.head())

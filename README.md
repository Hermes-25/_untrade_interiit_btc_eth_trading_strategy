
# Zelta Automations: Algorithmic Trading Strategies for BTC & ETH

## Introduction

This project explores advanced algorithmic trading strategies for the cryptocurrency market, focusing on BTC/USDT and ETH/USDT pairs. It leverages classical statistical techniques and reinforcement learning (RL) methods to design, test, and optimize strategies for both assets. The ETH strategy is heavily influenced by BTC's market behavior, while the BTC strategy is built upon Q-learning reinforcement learning.

## Table of Contents

- [Introduction](#introduction)
- [Project Structure](#project-structure)
- [Installation](#installation)
- [Usage](#usage)
- [Features](#features)
- [Datasets](#datasets)
- [ETH Strategy Details](#eth-strategy-details)
- [BTC Strategy Details](#btc-strategy-details)
- [Risk Management](#risk-management)
- [Performance Metrics](#performance-metrics)
- [Troubleshooting](#troubleshooting)
- [Contributors](#contributors)
- [License](#license)

## Project Structure

```bash
├── main_1_eth.py          # ETH strategy: indicator-driven
├── main_btc.py            # BTC strategy: Q-learning based
├── exec_1_eth.ipynb       # ETH execution notebook
├── BTC_2019_2023_1h.csv   # BTC historical data
├── ETHUSDT_1h.csv         # ETH historical data
├── Team_67_ppt.pdf        # Presentation slides
├── Zelta_Final_Report.pdf # Final technical report
```

## Installation

1. Clone this repository
2. Install the required dependencies:
   ```bash
   pip install -r requirements.txt
   ```

### Required Packages

- numpy
- pandas
- pykalman
- hurst
- untrade
- scikit-learn
- matplotlib
- dateutil

## Usage

Run the ETH strategy:
```bash
python main_1_eth.py
```

Run the BTC strategy:
```bash
python main_btc.py
```

## Features

- BTC-ETH correlation modeling
- Kalman Filtering and CUSUM for regime detection
- Hurst Exponent, Bollinger Bands, ATR, RSI for ETH trading
- Q-learning agent for BTC with discrete state-action spaces
- Volatility-based trade filters and trailing stop-loss mechanisms
- Backtesting framework integrated with metrics and visualizations

## Datasets

- **BTC_2019_2023_1h.csv**: BTC hourly price and volume from 2019–2023.
- **ETHUSDT_1h.csv**: ETH hourly price and volume data.

These datasets are used for training, testing, and validating strategy performance over historical windows (2020-2023).

## ETH Strategy Details

### Indicators Used

- **BTC indicators**: RSI, ATR, Bollinger Bands, Supertrend, Hurst, CUSUM
- **ETH indicators**: Hurst Exponent, Supertrend

### Entry Criteria

- BTC RSI > 70
- BTC Supertrend indicates bullish
- BTC-ETH correlation > 0.6
- ETH Hurst > 0.5
- BTC ATR < 1% of BTC open price

### Exit Criteria

- Trailing stop-loss hit
- BTC RSI < 30
- BTC Supertrend turns bearish
- 28-day max holding time exceeded

## BTC Strategy Details

Built using a **Q-learning** model with the following:

### State Space

- RSI signal (3 bins)
- Aroon signal (3 bins)
- EMA signal (3 bins)
- Holdings position (long/short/neutral)
- Price % change (20 bins)

### Action Space

- 0: Hold
- 1: Enter Long
- 2: Exit Long
- 3: Enter Short
- 4: Exit Short

### Reward Function

- Profit/loss after commission
- Heavy penalty on invalid trades or losses
- Reward shaped by net-worth change

## Risk Management

- **Trailing Stop-Loss** for long/short positions
- **ATR-Based Exit** if volatility exceeds 2.5% of BTC price
- **Time-Based Exit** after 28 days
- **Cooldown Period** of 24 hours after stop-loss trigger

## Performance Metrics

### ETH Strategy (2020–2023)

- **Net Returns**: 7684.52%
- **Sharpe Ratio**: 5.966
- **Sortino Ratio**: 19.67
- **Max Drawdown**: 17.14%
- **Total Trades**: 162

### BTC Strategy (2023–2024)

- **Net Returns**: 224.90%
- **Sharpe Ratio**: 9.153
- **Sortino Ratio**: 26.95
- **Win Rate**: 64.51%
- **Max Drawdown**: 13.50%

## Troubleshooting

- Ensure all CSV paths are correctly specified
- Check for package compatibility and version mismatches


## License

This project is intended for academic and educational use. License terms may vary.

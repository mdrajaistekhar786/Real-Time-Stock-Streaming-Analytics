# Real-Time Stock Streaming Analytics System

A real-time stock market analytics platform built using Python that processes continuously incoming financial data streams and identifies top-performing stocks using streaming algorithms and memory-efficient analytics techniques.

This project combines concepts from:

- Real-time data streaming
- Big data algorithms
- Financial analytics
- Quantitative systems
- Streaming computation
- Probabilistic algorithms
- Data engineering

The system was designed as part of the ED417 — Algorithms for Big Data course at BIT Mesra and demonstrates how modern financial systems process live market data efficiently without storing massive historical datasets.

---

# Table of Contents

1. Project Overview
2. Problem Statement
3. Objectives
4. System Architecture
5. Data Source
6. Methodology
7. Hybrid Sampling Strategy
8. Mini-Batch Processing
9. Rolling Window Storage
10. Feature Engineering
11. Scoring Model
12. Misra-Gries Algorithm
13. Real-Time Dashboard
14. Technologies Used
15. Project Structure
16. Results and Findings
17. Limitations
18. Future Improvements
19. Learning Outcomes
20. Conclusion

---

# Project Overview

Stock markets generate huge amounts of data every second. Traditional systems that store all incoming information become memory-intensive and computationally expensive.

This project demonstrates a lightweight real-time streaming analytics system capable of:

- Processing continuously arriving stock data
- Performing dynamic financial analysis
- Ranking stocks in real time
- Identifying consistent top performers
- Operating with limited memory

Instead of storing complete historical records, the system processes stock information dynamically using streaming-based techniques.

The project simulates how real-world financial analytics systems monitor live market activity efficiently.

---

# Problem Statement

Financial markets generate continuous streams of rapidly changing stock prices and trading volumes.

The challenge is:

> How can we analyze streaming stock market data and identify the best-performing stocks in real time without storing the entire dataset?

Key challenges addressed in this project:

- Massive continuously arriving data
- Limited memory availability
- Need for real-time decision making
- Dynamic ranking of stocks
- Efficient stream processing

The project focuses on building a memory-efficient streaming analytics pipeline capable of handling live financial data dynamically.

---

# Objectives

The main objectives of this project are:

## 1. Real-Time Processing

Process continuously arriving stock market data with minimal delay.

## 2. Financial Analytics

Compute important financial metrics such as:

- Return
- Volatility
- Risk-adjusted return
- Trading volume analysis

## 3. Dynamic Ranking

Continuously identify top-performing stocks in real time.

## 4. Memory Efficiency

Use streaming algorithms that require very limited memory.

## 5. Real-Time Visualization

Display live analytics results using continuously updating dashboards.

---

# System Architecture

The system follows a streaming pipeline architecture.

```text
Hybrid Sampling
       ↓
Fetch Data from NSE API
       ↓
Rolling Window Storage
       ↓
Feature Engineering
       ↓
Weighted Scoring
       ↓
Misra-Gries Streaming Algorithm
       ↓
Real-Time Visualization
```

The pipeline continuously runs in iterations, making the project behave like a true real-time streaming analytics engine.

---

# Data Source

The project uses stock-related information from the National Stock Exchange (NSE) of India.

## API Used

```text
https://www.nseindia.com/api/quote-equity?symbol=STOCK_NAME
```

## Data Collected

- Last traded price
- Trading volume
- Market activity indicators

The project uses secure HTTP requests with proper headers for stable communication with the NSE servers.

---

# Methodology

The project follows multiple stages for real-time stock stream analysis.

---

# 1. Hybrid Sampling Strategy

Instead of selecting stocks purely randomly, the system combines:

## Random Sampling

Ensures diversity and exploration across different stocks.

Advantages:

- Prevents bias
- Explores broader market activity
- Avoids repetitive selection

## Volume-Based Sampling

Prioritizes actively traded stocks with higher market participation.

Advantages:

- More reliable data
- Better liquidity indicators
- Higher investor activity

## Final Hybrid Strategy

The system selects stocks using both methods together to balance:

- Exploration
- Reliability
- Market importance

---

# 2. Mini-Batch Processing

Instead of processing only one stock at a time, the system processes multiple stocks during each iteration.

Benefits:

- Faster data collection
- Better comparison across stocks
- More stable streaming behavior
- Efficient real-time updates

This improves overall system performance significantly.

---

# 3. Rolling Window Storage

The system stores only the most recent 50 observations for each stock.

## Why Rolling Windows?

Storing all historical data is expensive and unnecessary for real-time streaming systems.

## Advantages

- Reduces memory consumption
- Improves computational speed
- Focuses on recent market behavior
- Makes analytics more responsive

Older records are automatically discarded as new data arrives.

---

# Feature Engineering

Raw stock prices alone are insufficient for meaningful financial analysis.

Therefore, the system computes multiple financial indicators dynamically.

---

## Financial Metrics Used

### Return

Measures percentage price change over time.

```text
Return = (Pt − Pt−1) / Pt−1
```

---

### Average Return

Represents overall growth trend of the stock.

---

### Volatility

Measures price fluctuation and risk.

Higher volatility implies:

- Greater uncertainty
- Higher investment risk

---

### Risk-Adjusted Return

Measures return relative to volatility.

This helps identify stocks that provide stable returns with lower risk.

---

### Volume Factor

Trading volume is normalized using logarithmic scaling:

```text
log(1 + Volume)
```

This prevents extremely large volume values from dominating the scoring system.

---

# Scoring Model

The project combines multiple financial indicators into a single weighted score.

## Formula

```text
Score = 0.5 × Return − 0.2 × Volatility + 0.3 × Volume
```

---

## Interpretation

### Return (Positive Weight)

Higher returns increase stock ranking.

---

### Volatility (Negative Weight)

Highly unstable stocks are penalized.

---

### Volume (Positive Weight)

Actively traded stocks receive higher confidence.

---

## Goal of the Scoring Model

The scoring system balances:

- Profitability
- Stability
- Liquidity

This creates a more realistic real-time stock evaluation mechanism.

---

# Misra-Gries Streaming Algorithm

The core streaming algorithm used in this project is the Misra-Gries Algorithm.

---

# Why Misra-Gries?

The algorithm is highly suitable for streaming environments because:

- Works directly on streaming data
- Requires very limited memory
- Avoids storing full history
- Efficiently identifies consistent top performers

---

# How the Algorithm Works

The algorithm maintains only a small set of candidate stocks.

### If stock already exists:
Increase its score.

### If free space exists:
Add the stock.

### If memory is full:
Reduce all scores and remove weak candidates.

Over time:

- Weak performers disappear
- Consistent strong performers survive

This makes the algorithm highly efficient for large streaming systems.

---

# Real-Time Dashboard

The project includes live visualization of streaming stock analytics using matplotlib dashboards.

## Dashboard Displays

- Top returns
- Highest volatility
- Best risk-adjusted returns
- Top streaming stocks
- Misra-Gries outputs

The dashboard continuously updates during execution.

---

# Technologies Used

## Programming Language

- Python

---

## Libraries

- pandas
- numpy
- matplotlib
- requests
- selenium
- scikit-learn

---

# Concepts Implemented

- Streaming Algorithms
- Big Data Processing
- Financial Analytics
- Quantitative Systems
- Approximate Computing
- Data Stream Mining
- Real-Time Analytics

---

# Project Structure

```text
Real-Time-Stock-Streaming-Analytics/
│
├── notebooks/
│   ├── 01_data_collection.ipynb
│   ├── 02_streaming_algorithms.ipynb
│   ├── 03_hyperloglog_monitoring.ipynb
│   └── 04_real_time_stock_analytics.ipynb
│
├── src/
│   ├── api/
│   ├── algorithms/
│   ├── analytics/
│   └── utils/
│
├── data/
│
├── outputs/
│
├── README.md
├── requirements.txt
└── LICENSE
```

---

# Results and Findings

The project successfully demonstrated:

## 1. Efficient Streaming Analytics

Real-time stock analysis without storing massive datasets.

---

## 2. Stable Performance Ranking

The scoring model effectively balanced:

- Return
- Risk
- Liquidity

---

## 3. Memory Efficiency

Rolling windows and streaming algorithms significantly reduced memory usage.

---

## 4. Consistent Performer Detection

Misra-Gries successfully identified stocks that consistently performed well across iterations.

---

# Limitations

Although effective, the project has some limitations.

## Limited Stock Coverage

Only a subset of stocks is analyzed during each iteration.

---

## Sequential API Calls

Stocks are fetched sequentially, which is slower than parallel processing.

---

## API Dependency

System performance depends on NSE API availability.

---

## Short-Term Analysis

Rolling windows focus mainly on recent behavior rather than long-term trends.

---

# Future Improvements

Several improvements can further enhance the project.

## Planned Enhancements

- Kafka integration
- Spark Streaming
- Parallel API processing
- Machine learning-based prediction
- Portfolio optimization
- Risk management systems
- Cloud deployment
- Interactive web dashboard

---

# Learning Outcomes

This project provided practical experience in:

- Real-time data streaming
- Financial analytics
- Big data algorithms
- Streaming computation
- Memory-efficient systems
- Quantitative analytics
- Data engineering workflows

---

# Conclusion

This project successfully demonstrates a memory-efficient real-time stock analytics system using streaming data processing techniques.

The combination of:

- Financial feature engineering
- Streaming computation
- Hybrid sampling
- Rolling windows
- Misra-Gries algorithm

creates an efficient framework for dynamic stock analysis.

The project highlights how modern streaming systems can process continuously arriving financial data efficiently without requiring massive storage resources.

---

# Author

## Md Raja Istekhar

- BIT Mesra Ranchi
- ED417 — Algorithms for Big Data

---

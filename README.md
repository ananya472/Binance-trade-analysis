# Binance-trade-analysis

**Trade Data Analysis and Account Ranking Report**

## **1. Introduction**
This report details the approach and findings of an analysis conducted on trade data to evaluate financial performance, extract key features, and rank accounts based on their profitability and risk-adjusted returns. The study employs data preprocessing, feature engineering, data visualization, and machine learning techniques using the XGBoost model.

## **2. Approach**

### **2.1 Data Preprocessing**
- The `Trade_History` column, initially stored as a JSON string, was converted into a list of dictionaries.
- The trade history data was exploded to create separate rows for each trade.
- The timestamps were converted to proper datetime formats.

### **2.2 Feature Engineering**
Key financial metrics were computed for each account to assess performance:
1. **Return on Investment (ROI)**: Measures the profitability of trades relative to the capital invested.
2. **Profit and Loss (PnL)**: The net gain or loss from trades.
3. **Win Rate**: The proportion of profitable trades.
4. **Maximum Drawdown (MDD)**: The largest peak-to-trough decline during the trading period.
5. **Sharpe Ratio**: A measure of risk-adjusted returns.
These metrics were stored in a structured CSV file (`account_metrics.csv`).

### **2.3 Data Visualization**
- A correlation heatmap was generated to analyze relationships between key metrics.
- Findings from the correlation analysis indicated strong dependencies between PnL, ROI, and Sharpe Ratio.

### **2.4 Machine Learning Approach (XGBoost Feature Importance Model)**
- An XGBoost regressor was trained to predict `PnL` using `ROI`, `Sharpe_Ratio`, and `MDD`.
- The model was fitted on processed data, and feature importance was extracted.
- The importance scores were normalized to derive a **Performance Score**.

### **2.5 Ranking Algorithm**
- The Performance Score was computed using the weighted feature importance.
- Accounts were ranked based on this score.
- The **top 20 ranked accounts** were identified for further analysis.

## **3. Findings**
- **ROI and Sharpe Ratio** had the highest contribution to `PnL`, confirming that profitability and risk-adjusted returns are key drivers of success.
- **Maximum Drawdown (MDD)** negatively impacted the Performance Score, indicating that accounts with large drawdowns should be penalized.
- The ranking system successfully identified the best-performing accounts, providing a reliable method for evaluating traders.



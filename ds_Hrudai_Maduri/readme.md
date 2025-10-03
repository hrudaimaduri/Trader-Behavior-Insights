# Trader Behavior & Market Sentiment Analysis
## Hyperliquid Trading Data Analysis Report

**Analyst:** [Hrudai Mauuri]  
**Date:** October 3, 2025  
**Assignment:** Junior Data Scientist - Trader Behavior Insights

---

## Executive Summary

This analysis examines the relationship between trader performance on Hyperliquid and Bitcoin market sentiment (Fear & Greed Index) over the period from **[e.g., Feb 2018]** to **[e.g., May 2025]**. The study analyzed **211,224** trades from **[Run: trader_data['Account'].nunique()]** unique traders, totaling **$[Run: trader_data['Size USD'].sum()/1e6]M** in trading volume.

### Key Findings:
**FILL IN AFTER RUNNING ANALYSIS:**
- ✅ **[Fear/Greed]** sentiment yields **[+15%]** higher average PnL than **[opposite sentiment]**
- ✅ Top 20 traders maintain **[65%]** win rate vs **[48%]** market average
- ✅ Optimal trading hours: **[14:00 - 16:00 IST]** show **[25%]** higher profitability
- ✅ **[BUY/SELL]** direction shows strongest performance with **[52%]** win rate

> **HOW TO FILL:** Run your complete analysis code, then copy numbers from these outputs:
> - Sentiment performance: `daily_trader_metrics.groupby('Sentiment')['Total_PnL'].mean()`
> - Win rates: `top_20_traders['Win_Rate'].mean()` vs `daily_trader_metrics['Win_Rate'].mean()`
> - Best hours: `merged_clean.groupby('Hour')['Closed PnL'].mean().idxmax()`
> - Direction: `merged_clean.groupby('Direction')['Is_Profitable'].mean()`

---

## Table of Contents

1. [Introduction](#introduction)
2. [Data Overview](#data-overview)
3. [Methodology](#methodology)
4. [Analysis Results](#analysis-results)
   - Sentiment-Performance Relationship
   - Top Trader Identification
   - Pattern Discovery
   - Temporal Analysis
5. [Key Insights](#key-insights)
6. [Strategic Recommendations](#strategic-recommendations)
7. [Conclusions](#conclusions)
8. [Appendix](#appendix)

---

## 1. Introduction

### Background
Hyperliquid is a decentralized derivatives exchange that enables traders to take leveraged positions on cryptocurrency markets. Understanding how trader behavior correlates with market sentiment is crucial for:
- Developing better trading strategies
- Risk management optimization
- Identifying profitable patterns
- Platform feature improvements

### Objectives
This analysis aims to:
1. Quantify the relationship between market sentiment and trading performance
2. Identify characteristics of successful traders
3. Discover hidden patterns in trading behavior
4. Provide actionable insights for strategy optimization

---

## 2. Data Overview

### Dataset Specifications

**Historical Trader Data:**
- **Records:** [211,224] trades
- **Traders:** [XXX] unique accounts
- **Timespan:** [Date Range]
- **Key Columns:** Account, Coin, Execution Price, Size, Side, Timestamp, Start Position, Closed PnL, Direction

**Fear & Greed Index Data:**
- **Records:** [2,644] daily sentiment readings
- **Timespan:** [Date Range]
- **Classifications:** Fear, Extreme Fear, Greed, Extreme Greed
- **Coverage:** [XX%] overlap with trading data

### Data Quality
- ✅ No missing values in critical columns
- ✅ Timestamp formats successfully standardized
- ✅ [X%] of trades have corresponding sentiment data
- ⚠️ [List any data quality issues found]

---

## 3. Methodology

### 3.1 Data Preprocessing
```python
1. Load and inspect both datasets
2. Convert timestamps to standardized datetime format
3. Extract date components for merging
4. Merge datasets on date
5. Handle missing values and outliers
```

### 3.2 Feature Engineering
Created derived metrics:
- **Win Rate:** Percentage of profitable trades
- **PnL per Trade:** Average profitability per trade
- **Trade Volume:** USD value of positions
- **Sentiment Categories:** Extreme Fear, Fear, Neutral, Greed, Extreme Greed
- **Temporal Features:** Hour, Day of Week, Month

### 3.3 Analysis Framework
1. **Sentiment-Performance Analysis:** Aggregated metrics by sentiment condition
2. **Trader Scoring System:**
   - PnL Score (50%)
   - Consistency Score - Win Rate (30%)
   - Volume Score (20%)
3. **Pattern Discovery:** Statistical analysis of temporal, directional, and symbol patterns
4. **Visualization:** Comprehensive charts and dashboards

---

## 4. Analysis Results

### 4.1 Sentiment-Performance Relationship

**Table 1: Performance Metrics by Market Sentiment**

| Sentiment | Avg PnL | Median PnL | Win Rate | Avg Trades | Total Volume |
|-----------|---------|------------|----------|------------|--------------|
| Extreme Fear | $XX.XX | $XX.XX | XX.X% | XX | $X.XXM |
| Fear | $XX.XX | $XX.XX | XX.X% | XX | $X.XXM |
| Greed | $XX.XX | $XX.XX | XX.X% | XX | $X.XXM |
| Extreme Greed | $XX.XX | $XX.XX | XX.X% | XX | $X.XXM |

**Key Observation:** [Describe which sentiment condition performs best and why]

![Sentiment Performance Chart](sentiment_performance.png)

**Statistical Significance:**
- [Perform t-test or ANOVA between sentiment groups]
- p-value: [X.XXX]
- Conclusion: [Statistically significant / Not significant]

### 4.2 Top Trader Identification

**Top 20 Traders Characteristics:**
- Average Win Rate: **[XX.X%]** (vs market avg [XX.X%])
- Average Number of Trades: **[XXX]**
- Average PnL per Trade: **$XX.XX**
- Combined Total PnL: **$XXX,XXX**

**Table 2: Top 10 Traders**

| Rank | Trader ID | Total PnL | Win Rate | # Trades | Overall Score |
|------|-----------|-----------|----------|----------|---------------|
| 1 | Trader_1 | $XX,XXX | XX.X% | XXX | XX.X |
| 2 | Trader_2 | $XX,XXX | XX.X% | XXX | XX.X |
| ... | ... | ... | ... | ... | ... |

![Top Traders Analysis](top_traders_analysis.png)

**Common Success Patterns:**
1. [Pattern 1: e.g., Moderate leverage usage 5-15x]
2. [Pattern 2: e.g., Consistent trading frequency]
3. [Pattern 3: e.g., Diversification across multiple coins]
4. [Pattern 4: e.g., Higher activity during favorable sentiment]

### 4.3 Sentiment Adaptation Analysis

**How Top Traders Adapt to Market Conditions:**

| Sentiment | Avg Win Rate (Top) | Avg Win Rate (All) | Difference |
|-----------|-------------------|-------------------|-----------|
| Extreme Fear | XX.X% | XX.X% | +X.X% |
| Fear | XX.X% | XX.X% | +X.X% |
| Greed | XX.X% | XX.X% | +X.X% |
| Extreme Greed | XX.X% | XX.X% | +X.X% |

**Insight:** Top traders maintain [higher/lower] win rates during [sentiment condition] by [strategy description].

### 4.4 Pattern Discovery

#### A. Temporal Patterns

**Best Trading Hours (IST):**
1. **Hour [XX]:00 - [XX]:00:** Highest average PnL ($XX.XX)
2. **Hour [XX]:00 - [XX]:00:** Highest trading volume
3. **Hour [XX]:00 - [XX]:00:** Best win rate (XX.X%)

**Day of Week Performance:**
| Day | Avg PnL | Total Volume | # Trades |
|-----|---------|--------------|----------|
| Monday | $XX.XX | $X.XXM | XXX |
| Tuesday | $XX.XX | $X.XXM | XXX |
| Wednesday | $XX.XX | $X.XXM | XXX |
| Thursday | $XX.XX | $X.XXM | XXX |
| Friday | $XX.XX | $X.XXM | XXX |
| Saturday | $XX.XX | $X.XXM | XXX |
| Sunday | $XX.XX | $X.XXM | XXX |

![Temporal Patterns](temporal_patterns.png)

**Key Finding:** Trading activity peaks on [Day] with [describe pattern]. PnL is highest during [timeframe], suggesting [interpretation].

#### B. Symbol/Coin Analysis

**Top 10 Performing Coins:**
| Rank | Coin | Total PnL | Win Rate | # Trades | Avg Trade Size |
|------|------|-----------|----------|----------|----------------|
| 1 | @107 | $XX,XXX | XX.X% | XXX | $XXX |
| 2 | [Coin] | $XX,XXX | XX.X% | XXX | $XXX |
| 3 | [Coin] | $XX,XXX | XX.X% | XXX | $XXX |
| ... | ... | ... | ... | ... | ... |

**Insight:** [@107] dominates trading volume, accounting for [XX%] of all trades. However, [other coin] shows [higher/lower] profitability per trade.

#### C. Direction Analysis (Long vs Short)

| Direction | Avg PnL | Win Rate | # Trades | Total Volume |
|-----------|---------|----------|----------|--------------|
| BUY (Long) | $XX.XX | XX.X% | XXX,XXX | $X.XXM |
| SELL (Short) | $XX.XX | XX.X% | XXX,XXX | $X.XXM |

**Finding:** [Long/Short] positions show [better/worse] performance with [X%] higher win rate. This suggests [market bias interpretation].

#### D. Position Size Analysis

**PnL Distribution by Trade Size:**
| Size Category | Avg PnL | Win Rate | Count |
|---------------|---------|----------|-------|
| Small (<$100) | $XX.XX | XX.X% | XXX |
| Medium ($100-$1K) | $XX.XX | XX.X% | XXX |
| Large ($1K-$10K) | $XX.XX | XX.X% | XXX |
| Very Large (>$10K) | $XX.XX | XX.X% | XXX |

**Insight:** [Interpretation of optimal position sizing]

---

## 5. Key Insights

### 🎯 Primary Discoveries

#### 1. Sentiment as a Performance Predictor
**Finding:** Market sentiment has a [strong/moderate/weak] correlation with trading performance.
- **Best Condition:** [Sentiment] yields average PnL of $[XX.XX] (+[X%] vs overall)
- **Worst Condition:** [Sentiment] yields average PnL of $[XX.XX] (-[X%] vs overall)
- **Statistical Significance:** p < [0.05] (statistically significant)

**Implication:** Traders can improve profitability by [X%] by adjusting position sizes or frequency based on sentiment readings.

#### 2. Success Profile: What Makes a Top Trader
Based on analysis of the top 20 traders, successful traders exhibit:

✅ **Higher Win Rate:** [XX%] vs [XX%] market average (+[X%] percentage points)  
✅ **Consistent Activity:** Average [XX] trades per day vs [XX] for others  
✅ **Better Risk Management:** Lower PnL volatility ($[XX] vs $[XX])  
✅ **Moderate Leverage:** Prefer [X-X]x leverage range  
✅ **Diversification:** Trade [X] different coins on average vs [X] for others  

**Most Distinguishing Factor:** [Describe the #1 differentiator]

#### 3. Hidden Patterns Uncovered

**Pattern A - Temporal Edge:**
- Trading between [HH:00-HH:00 IST] shows [XX%] better performance
- [Day] consistently outperforms other days by [XX%]
- Weekend trading shows [increased/decreased] volatility

**Pattern B - Sentiment Arbitrage:**
- Extreme sentiment conditions (both fear and greed) show [higher/lower] volatility
- Win rate improves by [X%] during transitional sentiment periods
- Top traders increase activity by [XX%] during [sentiment condition]

**Pattern C - Coin Selection:**
- [@107] dominates but [other coin] offers better risk-adjusted returns
- Diversification across [X+] coins reduces drawdowns by [XX%]
- Altcoin trading shows [higher/lower] win rates but [greater/lesser] PnL variance

**Pattern D - Position Management:**
- Closing positions within [X] hours shows [XX%] better outcomes
- Scaling into positions (multiple entries) improves win rate by [X%]
- [Long/Short] bias varies by [X%] depending on sentiment

#### 4. Risk-Reward Dynamics

**Sharpe-like Metrics:**
- Top Traders: Average return/volatility ratio of [X.XX]
- All Traders: Average return/volatility ratio of [X.XX]
- **Difference:** Top traders achieve [XX%] better risk-adjusted returns

**Maximum Drawdown Analysis:**
- Top traders experience [XX%] lower maximum drawdowns
- Recovery time is [XX%] faster for successful traders

---

## 6. Strategic Recommendations

### 🎯 For Traders

#### Recommendation 1: Sentiment-Aware Position Sizing
**Action:** Adjust position sizes based on market sentiment
- **During [Favorable Sentiment]:** Increase position sizes by [20-30%]
- **During [Unfavorable Sentiment]:** Reduce positions by [30-40%] OR sit out
- **Expected Impact:** Potential [10-15%] improvement in overall PnL

#### Recommendation 2: Optimal Trading Windows
**Action:** Concentrate trading during identified high-performance periods
- **Primary Window:** [HH:00 - HH:00 IST]
- **Secondary Window:** [HH:00 - HH:00 IST]
- **Best Days:** [Day 1], [Day 2]
- **Expected Impact:** [5-10%] win rate improvement

#### Recommendation 3: Win Rate Threshold
**Action:** Target and maintain a minimum [52%] win rate
- Use stop-losses to prevent large losers
- Take partial profits on winners
- Review and adjust strategy if win rate falls below [50%] for [X] consecutive days
- **Expected Impact:** Sustainable long-term profitability

#### Recommendation 4: Diversification Strategy
**Action:** Trade [3-5] different coins to spread risk
- Primary focus: [@107] for liquidity
- Secondary: [Coin 2], [Coin 3] for better risk-adjusted returns
- Limit exposure to any single coin to [30%] of portfolio
- **Expected Impact:** [20-30%] reduction in portfolio volatility

#### Recommendation 5: Leverage Management
**Action:** Use moderate leverage in the [5-15x] range
- Avoid >20x leverage except during extremely favorable conditions
- Reduce leverage during high volatility periods
- Top traders average [10x] leverage
- **Expected Impact:** Lower risk of liquidation, more stable returns

### 🎯 For the Platform (Hyperliquid)

#### Recommendation 1: Sentiment Integration
**Feature:** Add real-time sentiment indicators to the trading interface
- Display current Fear & Greed Index
- Historical sentiment performance overlay on charts
- Sentiment-based trade alerts
- **Expected Value:** Enhanced trader decision-making, increased engagement

#### Recommendation 2: Trader Education
**Feature:** Create educational content based on successful patterns
- "Trading the Sentiment Cycle" guide
- Optimal timing workshops
- Risk management best practices from top traders
- **Expected Value:** Improved trader success rates, reduced churn

#### Recommendation 3: Smart Notifications
**Feature:** Alert system for optimal trading conditions
- Notify users during high-performance time windows
- Sentiment change alerts
- Volume spike notifications
- **Expected Value:** Increased active trading, better user outcomes

#### Recommendation 4: Performance Analytics Dashboard
**Feature:** Provide traders with their own performance metrics
- Win rate tracking
- Sentiment-adjusted performance
- Comparison to top trader benchmarks
- Risk metrics (Sharpe ratio, max drawdown)
- **Expected Value:** Data-driven improvement, user retention

---

## 7. Advanced Analysis & Future Work

### Machine Learning Opportunities

#### 1. Predictive Models
**Objective:** Predict trader success based on early behavior
- **Features:** First 10 trades, sentiment exposure, timing patterns
- **Model:** Random Forest / XGBoost classifier
- **Use Case:** Early identification of promising traders for platform support

#### 2. Sentiment-Based Strategy Optimization
**Objective:** Build algorithmic trading strategies around sentiment signals
- **Approach:** Reinforcement learning with sentiment as state variable
- **Expected Outcome:** Automated position sizing recommendations

#### 3. Trader Clustering
**Objective:** Segment traders into behavioral archetypes
- **Method:** K-means clustering on trading patterns
- **Applications:** Personalized recommendations, targeted education

### Additional Analyses to Consider

1. **Market Impact Analysis:** How do large trades affect prices?
2. **Copy Trading Patterns:** Identify potential leader-follower relationships
3. **Liquidation Analysis:** Patterns leading to position liquidations
4. **Fee Optimization:** Impact of trading fees on net profitability
5. **Cross-Exchange Arbitrage:** Opportunities vs other platforms

---

## 8. Conclusions

### Summary of Findings

This comprehensive analysis of Hyperliquid trading data reveals several critical insights:

1. **Sentiment Matters:** Market sentiment significantly impacts trading outcomes, with [sentiment] conditions yielding [XX%] better performance.

2. **Success is Systematic:** Top traders follow consistent patterns—moderate leverage, diversification, optimal timing, and >50% win rates.

3. **Hidden Opportunities:** Temporal patterns reveal specific hours and days with significantly better risk-reward profiles.

4. **Risk Management is Key:** The difference between profitable and unprofitable traders lies more in risk management than pure directional accuracy.

### Business Impact

**For Traders:**
- Clear, actionable strategies to improve profitability
- Data-driven approach to risk management
- Benchmark metrics for self-assessment

**For Platform:**
- Opportunity to enhance product features
- Data for trader education and retention
- Insights for marketing and growth strategies

### Final Thoughts

The cryptocurrency derivatives market is highly competitive, but this analysis demonstrates that systematic, data-driven approaches can provide meaningful edge. By understanding the relationship between market sentiment and trading behavior, traders can make more informed decisions and improve their risk-adjusted returns.

The patterns identified here are based on historical data and should be continuously validated and updated as market conditions evolve.

---

## 9. Appendix

### A. Technical Specifications

**Tools Used:**
- Python 3.x
- pandas, numpy (data manipulation)
- matplotlib, seaborn (visualization)
- scikit-learn (feature scaling)

**Code Repository:** [GitHub Link]

**Data Sources:**
- Hyperliquid Historical Trader Data (211,224 records)
- Bitcoin Fear & Greed Index (2,644 records)

### B. Statistical Methods

**Tests Performed:**
- Descriptive statistics (mean, median, std deviation)
- Group comparisons (sentiment categories)
- Correlation analysis
- [t-tests / ANOVA for significance testing]

### C. Limitations

1. **Data Scope:** Analysis limited to provided timeframe ([dates])
2. **Survivorship Bias:** Only active accounts included
3. **Market Conditions:** Results reflect specific market regime
4. **External Factors:** Doesn't account for news events, regulatory changes
5. **Causation:** Correlations identified don't prove causation

### D. Glossary

- **PnL:** Profit and Loss
- **Win Rate:** Percentage of trades that are profitable
- **Leverage:** Borrowed capital ratio (e.g., 10x = $10 position with $1 capital)
- **Fear & Greed Index:** Market sentiment indicator (0-100 scale)
- **Liquidation:** Forced position closure due to insufficient margin

### E. References

1. Alternative.me - Crypto Fear & Greed Index
2. Hyperliquid Documentation - Trading Mechanics
3. [Academic papers on sentiment analysis in crypto markets]
4. [Trading psychology and risk management literature]

---

## Contact Information

**Analyst:** [Your Name]  
**Email:** [Your Email]  
**LinkedIn:** [Your Profile]  
**GitHub:** [Repository Link]

**Submission Date:** October 3, 2025

---

## Appendix F: Code Samples

### Data Loading and Preprocessing
```python
# Load datasets
trader_data = pd.read_csv('historical_data.csv')
sentiment_data = pd.read_csv('fear_greed_index.csv')

# Convert timestamps
trader_data['DateTime'] = pd.to_datetime(
    trader_data['Timestamp IST'], 
    format='%d-%m-%Y %H:%M'
)
sentiment_data['DateTime'] = pd.to_datetime(
    sentiment_data['date'], 
    format='%d-%m-%Y'
)

# Extract dates for merging
trader_data['Date'] = trader_data['DateTime'].dt.date
sentiment_data['Date'] = sentiment_data['DateTime'].dt.date

# Merge datasets
merged_data = trader_data.merge(
    sentiment_data[['Date', 'classification', 'value']], 
    on='Date', 
    how='left'
)
```

### Top Trader Scoring Algorithm
```python
from sklearn.preprocessing import MinMaxScaler

scaler = MinMaxScaler(feature_range=(0, 100))

# Calculate component scores
trader_metrics['PnL_Score'] = scaler.fit_transform(
    trader_metrics[['Total_PnL']]
)
trader_metrics['Consistency_Score'] = trader_metrics['Win_Rate'] * 100
trader_metrics['Volume_Score'] = scaler.fit_transform(
    trader_metrics[['Total_Volume']]
)

# Weighted overall score
trader_metrics['Overall_Score'] = (
    trader_metrics['PnL_Score'] * 0.5 +
    trader_metrics['Consistency_Score'] * 0.3 +
    trader_metrics['Volume_Score'] * 0.2
)

# Get top 20
top_traders = trader_metrics.nlargest(20, 'Overall_Score')
```

---

**END OF REPORT**

---

### Submission Checklist

- [ ] All analysis completed and verified
- [ ] Visualizations generated and saved
- [ ] Report compiled with findings
- [ ] Code cleaned and documented
- [ ] GitHub repository created (or Google Drive folder)
- [ ] Resume updated and ready
- [ ] Cover email drafted
- [ ] All recipient emails confirmed

**Email Subject:** "Junior Data Scientist – Trader Behavior Insights"

**Recipients:**
- saami@bajarangs.com
- nagasai@bajarangs.com  
- chetan@bajarangs.com
- CC: sonika@primetrade.ai

**Attachments/Links:**
1. This report (PDF)
2. GitHub repository link OR Google Drive folder
3. Resume
4. Key visualizations

**Email Body Template:**
```
Dear Hiring Team,

I am excited to submit my analysis for the Junior Data Scientist position 
focused on Trader Behavior Insights.

My analysis of the Hyperliquid trading data and Bitcoin Fear & Greed Index 
has uncovered several actionable insights:

• [Key Finding 1]
• [Key Finding 2]  
• [Key Finding 3]

The complete analysis, including code, visualizations, and detailed 
findings, is available at: [Your GitHub/Drive Link]

I look forward to discussing these findings and how I can contribute to 
your team's success.

Best regards,
[Your Name]
[Your Contact Information]
```

**Good luck with your submission! 🚀**
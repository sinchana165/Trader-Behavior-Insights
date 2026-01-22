**Trader Behavior Insights: Performance vs Bitcoin Market Sentiment (Fear/Greed)**

**Objective**

Analyze the relationship between Bitcoin market sentiment (Fear/Greed Index) and trader performance using Hyperliquid historical trading data. The goal is to uncover behavior patterns and performance differences across sentiment regimes and provide actionable strategy insights. 

**Datasets Used**

1. **Bitcoin Market Sentiment Dataset** 
1. Columns: date, value, classification 
1. Source: Fear & Greed Index 
2. **Hyperliquid Historical Trader Dataset** 

a.  Columns: Account, Coin, Execution Price, Size USD, Side, Timestamp 

IST, Closed PnL, Fee, etc. 

**Approach**

1. **Data Cleaning & Preparation** 
- Converted sentiment dataset date to datetime format 
- Mapped sentiment classifications into:
- **Fear** = Fear + Extreme Fear 
- **Greed** = Greed + Extreme Greed 
- Converted trader timestamps (Timestamp IST) to datetime 
- Extracted date from timestamp for merging 
- Created additional features:
- is\_win (1 if Closed PnL > 0 else 0) 
- is\_loss (1 if Closed PnL < 0 else 0) 
2. **Merging Datasets** 
- Joined trader data with sentiment data using date 
- Removed trades with missing sentiment values after merge
3. **Analysis Performed** 
- Fear vs Greed comparison: 
- Total PnL 
- Average PnL per trade 
- Median PnL 
- Win rate 
- Average trade size (USD) 
- Average fee 
- Extreme Fear vs Extreme Greed analysis 
- Coin-wise performance for top traded coins
- Top 10% vs Bottom 10% trader behavior comparison
- Bootstrap test to estimate confidence interval for mean PnL difference

**Key Findings (Summary)**

- Greed days show higher profitability and slightly higher win rate compared to Fear days. 
- Fear days show larger average position sizes and higher average fees.
- Extreme Greed generally performs better than Extreme Fear.
- Top traders are more consistent, but sentiment still impacts performance.

**Recommendations**

- During **Fear**: 
- Reduce position sizing 
- Avoid overtrading 
- Control fee impact by improving execution discipline
- During **Greed**: 
  - Higher opportunity but maintain strict risk controls
  - Protect profits using stop-loss and position limits 
- Build sentiment-aware risk rules: 
- Dynamic leverage/size adjustment based on sentiment regime

**How to Run**

**Install dependencies** 

pip install -r requirements.txt 


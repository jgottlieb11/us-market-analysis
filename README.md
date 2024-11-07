# U.S. Stock Time Series Analysis

## Introduction

This project provides an in-depth analysis of daily log returns for U.S. stocks, utilizing data from the Finnhub and Yahoo Finance APIs. The primary goal was to capture a comprehensive view of the U.S. stock market by examining both days with price changes (non-zero log returns) and days with no changes (zero log returns). By incorporating both active trading days and periods with zero returns—resulting from low trading volume or lack of price movement—this analysis presents insights into the behavior of stocks across various activity levels, offering perspectives relevant to both long-term investors and short-term traders.

To handle the substantial dataset, I implemented the following preprocessing steps:
1. **Symbol Sampling**: Randomly sampled stocks to manage processing time while ensuring a diverse selection of stocks in terms of trading frequency and activity.
2. **Inclusion of Zero Returns**: Retained zero returns to assess the broader market behavior, capturing stocks with low trading volume and price changes, while also analyzing only non-zero returns to focus on patterns in active trading periods.
3. **Batch Processing**: Processed data in manageable batches to optimize performance and data handling.

---

## Aggregate Analysis

### Figure 1: Distribution of Mean Log Returns Across All Stocks
![Distribution of Mean Log Returns - Excluding Zero Log Returns](figures/meanlogreturnexcl.png)  
![Distribution of Mean Log Returns - Including Zero Log Returns](figures/meanlogreturnincl.png)

**Objective**: This plot examines the distribution of mean log returns across different stock symbols to observe general performance over the analyzed timeframe.

#### Methodology:
1. **Mean Log Return Calculation**: For each stock symbol, I calculated the mean of daily log returns to capture each stock's average return over the period.
2. **Separate Analyses with and without Zero Log Returns**:
   - *Including Zero Log Returns*: This includes all trading days, capturing stocks with low trading volumes that may not see daily price changes.
   - *Excluding Zero Log Returns*: Focuses on days with active trading, providing insights into stocks that experience more frequent price movements.

#### Key Observations and Insights:
- **Market Stability**: The concentration of returns around zero in both plots indicates market stability, with minimal overall gains or losses when aggregated across stocks.
- **Effect of Trading Frequency**: Including zero returns highlights low-activity stocks with low variation, while excluding them reveals the dynamics of more actively traded stocks.

---

### Figure 2: Volatility (Standard Deviation of Log Returns) Across Stocks
![Volatility (Standard Deviation of Log Returns) - Excluding Zero Log Returns](figures/volatilityexcl.png)  
![Volatility (Standard Deviation of Log Returns) - Including Zero Log Returns](figures/volatilityincl.png)

**Objective**: This plot evaluates the volatility of each stock’s returns, showing how much individual stocks fluctuate over time.

#### Methodology:
1. **Volatility Calculation**: Calculated the standard deviation of log returns for each stock symbol.
2. **Separate Analyses for Different Perspectives**:
   - *Including Zero Log Returns*: Captures low volatility in stocks with fewer daily price changes.
   - *Excluding Zero Log Returns*: Focuses on stocks with more consistent price movements, emphasizing periods of active trading.

#### Key Observations and Insights:
- **Distribution Shape**: The inclusion of zero returns skews the distribution toward lower volatility, representing low-activity stocks. Excluding zero returns reveals a wider range of volatility among frequently traded stocks.
- **Market Composition**: Including zero returns provides a conservative measure of market risk, while excluding zero returns highlights higher activity levels and potential short-term trading opportunities.

---

### Figure 3: Min vs. Max Log Returns for Each Stock
![Min vs Max Log Returns - Excluding Zero Log Returns](figures/minmaxexcl.png)  
![Min vs Max Log Returns - Including Zero Log Returns](figures/minmaxincl.png)

**Objective**: This scatter plot examines the range of log returns, focusing on the minimum and maximum returns for each stock.

#### Methodology:
1. **Minimum and Maximum Return Calculation**: For each stock, I identified the lowest and highest daily log returns to capture the range of price movement.
2. **Separate Analyses for Market Perspective**:
   - *Including Zero Log Returns*: Offers a broad view of return stability across the market.
   - *Excluding Zero Log Returns*: Focuses on variability during active trading periods.

#### Key Observations and Insights:
- **Stability vs. Activity**: Including zero returns shows that most stocks stay within a limited range, while excluding them emphasizes stocks prone to more extreme movements, which could appeal to risk-tolerant traders.

---

### Figure 4: Mean Log Return vs. Volatility (Standard Deviation of Log Return)
![Mean Log Return vs Volatility - Excluding Zero Log Returns](figures/meanvexcl.png)  
![Mean Log Return vs Volatility - Including Zero Log Returns](figures/meanvincl.png)

**Objective**: This scatter plot assesses the relationship between average return and volatility, exploring the risk-return profile of each stock.

#### Methodology:
1. **Return and Volatility Calculation**: Calculated each stock’s mean log return and volatility.
2. **Separate Analyses for Different Risk Perspectives**:
   - *Including Zero Log Returns*: Highlights low-risk, low-return stocks that seldom trade.
   - *Excluding Zero Log Returns*: Shows more variability among stocks with active trading.

#### Key Observations and Insights:
- **Risk-Return Tradeoff**: Most stocks have low returns and low volatility, but excluding zero returns reveals stocks with higher risk and potential reward, aligning with the traditional risk-return tradeoff principle.

---

### Figure 5: Correlation Matrix of Summary Statistics
![Correlation Matrix - Excluding Zero Log Returns](figures/confexcl.png)  
![Correlation Matrix - Including Zero Log Returns](figures/confincl.png)

**Objective**: This matrix explores the relationships between various statistical measures (mean, volatility, min, and max) for each stock.

#### Methodology:
1. **Correlation Calculation**: Generated correlations between each statistic to assess interdependencies.
2. **Separate Correlations for Broader and Active Market Perspectives**:
   - *Including Zero Log Returns*: Reflects stability across low-activity stocks.
   - *Excluding Zero Log Returns*: Emphasizes relationships within frequently traded stocks.

#### Key Observations and Insights:
- **Correlations Among Measures**: Strong relationships between min, max, and volatility in both cases indicate that volatile stocks tend to exhibit wider price swings. Excluding zero returns increases correlations, emphasizing the variability in active stocks.

---

### Figure 6: Autocorrelation Analysis (30-Day Lag)
![Autocorrelation - Excluding Zero Log Returns](figures/autoexcl.png)  
![Autocorrelation - Including Zero Log Returns](figures/autoincl.png)

**Objective**: This plot examines autocorrelation in returns to detect potential trends or mean-reverting behavior.

#### Methodology:
1. **Autocorrelation Calculation**: Calculated average autocorrelation up to a 30-day lag for each stock symbol.
2. **Separate Analyses for Market Dynamics**:
   - *Including Zero Log Returns*: Provides insight into overall market trends.
   - *Excluding Zero Log Returns*: Focuses on short-term trends in actively traded stocks.

#### Key Observations and Insights:
- **Mean-Reversion and Trend Behavior**: The rapid decay in autocorrelation, particularly when excluding zero returns, suggests a limited persistence in returns, aligning with efficient market assumptions.

---

### Figure 7: Day-of-Week Effect on Log Returns
![Day-of-Week Effect - Excluding Zero Log Returns](figures/weakexcl.png)  
![Day-of-Week Effect - Including Zero Log Returns](figures/weakincl.png)

**Objective**: This bar plot explores potential day-of-week effects on returns, identifying any patterns in daily performance.

#### Methodology:
1. **Mean Return by Day Calculation**: Calculated the average return for each weekday.
2. **Separate Analyses for Day-of-Week Patterns**:
   - *Including Zero Log Returns*: Reflects broader market patterns.
   - *Excluding Zero Log Returns*: Highlights patterns in actively traded stocks.

#### Key Observations and Insights:
- **Weekly Trends**: The analysis shows slight patterns, though due to the limited sample size, the findings are not universally applicable. Nevertheless, negative returns mid-week suggest a potential for behavioral trends.

---

### Figure 8: 30-Day Average Rolling Mean and Volatility Across All Stocks
![30-Day Rolling Mean and Volatility - Including Zero Log Returns](figures/30incl.png)  
![30-Day Rolling Mean and Volatility - Excluding Zero Log Returns](figures/30excl.png)

**Objective**: This figure shows rolling averages for mean and volatility to observe trends in returns and fluctuations over time.

#### Methodology:
1. **Rolling Mean and Volatility Calculation**: Computed a 30-day rolling mean and standard deviation for each stock symbol.
2. **Separate Analyses for Comprehensive Trends**:
   - *Including Zero Log Returns*: Captures stability across the market.
   - *Excluding Zero Log Returns*: Shows more variability in actively traded stocks.

#### Key Observations and Insights:
- **Market Stability and Activity**: The smooth volatility when including zero returns reflects market stability, while excluding zero returns reveals volatility spikes, potentially useful for short-term trading insights.

---

## Conclusion

This analysis offers a detailed view of the U.S. stock market’s performance, capturing both broad market stability and specific patterns in active trading periods. By including zero returns, the study presents a conservative measure of the market, ideal for understanding overall stability and the effect of low trading volume. In contrast, focusing on non-zero returns highlights the behavior of actively traded stocks, providing insights relevant to short-term trading and volatility. Although the dataset covers a small sample of U.S. stocks, this dual approach offers a balanced view of market behavior, suitable for various investment strategies.

---

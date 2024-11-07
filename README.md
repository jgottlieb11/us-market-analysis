# U.S. Stock Market Data Analysis

## Introduction

This project focuses on analyzing daily stock returns for U.S. stocks using time series log returns data. The data was retrieved using the Finnhub and Yahoo Finance APIs, and Python libraries like `pandas` and `matplotlib` were utilized to process and visualize meaningful trends. The goal was to conduct a holistic analysis, capturing both active and less active stocks to understand general market behavior while identifying specific patterns within subsets of stocks with varying trading frequencies.

## Data Preprocessing

Given the dataset’s extensive volume (over 500,000 observations), data processing presented challenges in terms of time and identifying clear patterns amid noise. To manage this, I implemented batch processing and random sampling by ticker symbol. Sampling helped reduce the data volume, facilitating clearer trend identification without distorting the dataset’s representation of the market. Both zero returns (periods with no price movement) and non-zero returns were kept, allowing for a broad analysis that includes low-volume stocks and actively traded ones.

## Aggregate Analysis

### Figure 1: Distribution of Mean Log Returns Across All Stocks

The histogram in Figure 1 illustrates the concentration of mean log returns around zero. Most stocks in the dataset have average returns close to zero, suggesting a balanced market state without extreme long-term gains or losses. This distribution often reflects a diversified portfolio effect, where individual fluctuations are offset by the broader market’s stability.

### Figure 2: Volatility (Standard Deviation of Log Returns) Across Stocks

Figure 2 shows the distribution of volatility, represented by the standard deviation of log returns across stocks. The plot reveals that most stocks exhibit low to moderate volatility, aligning with the risk-averse nature of many market participants who favor stable returns. The presence of a few highly volatile stocks as outliers suggests high-risk opportunities or market instability for specific stocks.

### Figure 3: Min vs. Max Log Returns for Each Stock

The scatter plot in Figure 3 provides insight into each stock’s minimum and maximum log returns, with most stocks clustering around a narrow range. This clustering highlights the relatively stable performance of most stocks, with limited fluctuations. However, outliers with extremely high maximum or low minimum returns indicate stocks with more pronounced fluctuations, reflecting high-risk, high-reward dynamics.

### Figure 4: Mean Log Return vs. Volatility (Standard Deviation of Log Return)

The relationship between mean log return and volatility in Figure 4 reveals a concentration of stocks at low average returns and low volatility, while a few stocks deviate as high-volatility outliers. This clustering suggests that stable stocks are predominant, while a few offer potential for higher gains at increased uncertainty. The risk-return tradeoff is evident here, where greater volatility is often accompanied by variable returns.

### Figure 5: Correlation Matrix of Summary Statistics

The correlation matrix in Figure 5 explores relationships among various summary statistics like mean log return, volatility, minimum, and maximum log returns. Notable insights include:

- Mean Log Return and Volatility: A slight negative correlation suggests that high average returns can occur without high volatility, offering potential for stable gains.
- Minimum and Maximum Returns: A strong positive correlation reflects that stocks with extreme high values also tend to have extreme low values, highlighting volatility.
- Volatility and Minimum Returns: The negative correlation suggests that more volatile stocks are more likely to experience low minimum returns, underlining the downside risk associated with volatility.

This matrix captures the interactions between volatility, returns, and risk measures across stocks, aiding in understanding how different financial statistics influence one another.

## Time Series Analysis

### Figure 6: Autocorrelation Analysis (30-Day Lag)

The autocorrelation plot in Figure 6 captures the persistence of returns over time. Short-term autocorrelation values are mild, reflecting weak correlations that rapidly decline across longer lags. This trend aligns with the weak-form efficient market hypothesis, where returns should exhibit minimal correlation over time. Minor initial autocorrelation could stem from market micr

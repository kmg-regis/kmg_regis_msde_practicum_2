# Kate Gallagher | Regis University | MSDE Practicum II

## Project Goal
My goal for this project was to determine if cryptocurrencies could be treated like traditional securities, and see how equity trading strategies performed when applied to cryptocurrency-based portfolios. 

As someone with a background in traditional portfolio management and equities trading, I have always been skeptical of cryptocurrencies as an investment vehicle. Cryptocurrency is “fake internet money” that is worth real money, yet it doesn’t represent a share of a company or a claim on assets the way that true securities do. Unlike securities trading, crypto trading is a complex process that takes an unpredictable and varying amount of time. It is also hard to use as actual currency, since there are only a few places in the world that accept it, and it is difficult to liquidate to USD. 

Crypto was invented as a way to decentralize the financial system, and circumvent traditional institutions and trading methods. This can be a good thing – for example, the banks that service developing nations often have high fees, long delays, and are prone to collapse, so the people in these nations often turn to crypto as a way to have greater control over their money. It can also be a bad thing – crypto transactions are anonymous, so it is used to fund weapons sales to terrorist groups, drug trafficking, human trafficking, etc. 

Ultimately, there are two mindsets about the usage of crypto that are inherently at odds with each other: crypto as a currency to transact with, and crypto as a trading vehicle to invest in and profit on. As a skeptic, I decided to dig into the concept of crypto as a trading vehicle to see if it has merit.

## Backtesting Engine Design
I created a set of Python class objects that interact with each other as shown in the diagram below. The full details of the class objects including their attributes and methods can be found in my UML diagram file. 	
![engine_graph](https://github.com/kmg-regis/kmg_regis_msde_practicum_2/blob/main/images/engine_graph.png)

## Portfolio Setup
I decided on seven cryptocurrencies to track:

•	<b>Bitcoin</b> (BTC) & <b>Ethereum</b> (ETH): oldest, established, relatively stable

•	<b>Dogecoin</b> (DOGE) & <b>Shiba Inu</b> (SHIB): meme coins, started as jokes

•	<b>Solana</b> (SOL) & <b>Cardano</b> (ADA) & <b>Ripple</b> (XRP): newest, more volatile

I also pulled <b>S&P 500</b> pricing data to see how these currencies perform against a basic equity standard.

Using these, I developed seven different trader profiles:

•	<u>Simple Trader</u>: trades only one currency (one of each)

•	<u>Standard Trader</u>: BTC & ETH only

•	<u>Meme Trader</u>: DOGE & SHIB only

•	<u>Cutting Edge Trader</u>: SOL, ADA & XRP only

•	<u>Diversified Trader</u>: All 7 cryptocurrencies

•	<u>Traditional Trader</u>: S&P 500 only

This configuration represents twelve different portfolios: one for each single currency, plus the combination portfolios, plus the S&P portfolio.

The currencies represented a wide range of USD prices, so I set the increments of each to be roughly equal at the beginning of the test. For portfolios with more than one currency, I set the increments the way a reasonably informed investor with no view of future performance might. The full details of the currency balances can be found in my Performance Test Results excel file.

## Strategy Design
I designed four trading strategies to test against my data:
![strategy_setup](https://github.com/kmg-regis/kmg_regis_msde_practicum_2/blob/main/images/strategy_setup.png)

•	Each portfolio starts with <b>$100k USD cash on 1/1/2023

•	The testing runs from <b>1/1/2023</b> to <b>2/29/2024</b>

•	Transaction fees are fixed at <b>0.1%</b>; slippage is fixed at <b>0.05%</b>

•	Trades execute at <u>midpoint between high and low price</u> for the time period. 

## Data Sources
Unlike equity markets, crypto trading platforms are siloed and do not share pricing data. To account for price disparity between platforms, I pulled historic pricing data from two of the “most trusted” crypto trading platforms, according to Coinmarketcap.com: Binance and Coinbase. My S&P 500 pricing data came from Yahoo Finance. 

The historic pricing data included open, close, high, and low price for each time period: Binance provided this data for every 4 hours continuously, and Coinbase every 6 hours. The S&P data was provided daily.

I ran each of the 4 strategies on the 11 crypto portfolios, for two different datasets, totaling 88 crypto performance tests, plus 4 strategies on the S&P portfolio, for a total of 92 performance tests.  

The results of each individual test can be found in my Performance Test Results excel file. 


There was a <u>36% mean difference</u> in performance results between the Binance and Coinbase data. This massive disparity can be explained by several factors:

•	As mentioned, crypto trading platforms are siloed and do not share pricing data

•	Binance has about 10x the trade volume and 8x the weekly visitors of Coinbase, meaning prices on Binance are likely more reflective of the true market price

•	The more volatile currencies had greater price disparity than the more stable ones

•	The shorter time window of the Binance data captured more volatility

This does mean that there are opportunities to profit via cross-platform arbitrage, but it is a risky and complex process due to the unpredictable amount of time that transactions take.

## Results by Strategy
 
![strategy_perf_table](https://github.com/kmg-regis/kmg_regis_msde_practicum_2/blob/main/images/strategy_perf_table.png)

The table above displays the mean performance for each strategy, as well as the best & worst performance, and the S&P 500 portfolio performance for comparison. 

•	<b>Buy & Hold</b> performed best overall
   
   o	Heavily boosted by SOL, which grew by over 1000% 
   
   o	This is an unrealistic approach to trading, but it shows how much of the performance of each strategy can be attributed to the overall market growth.

•	<b>Momentum</b> was the big surprise with very high performance

  o	As a “bandwagon strategy” (buy when it’s rising, sell when it’s dipping), I expected it to do poorly – but due to high market volatility, it profited 

  o	Momentum trading requires constant price monitoring and quick reactions to market changes
  
  o	The S&P 500 performance was flat because it never hit the 10% volatility threshold to trigger a buy or a sell – meaning the close price was never 10% higher or lower than the previous day’s close price. This is normal for equities.

•	<b>Dollar Cost Averaging</b> had the most consistent returns overall, as seen in the density distribution chart below. 

•	<b>Moving Average Crossover</b> performed worst, but still got great returns overall

 o	S&P performance was flat because a buy was never triggered. This is understandable, since MAC is a strategy usually applied to multiple individual stocks in a portfolio, rather than an index fund which has steadier performance due to being a composite.

 o	Accordingly, the MAC strategy performed best with the diversified crypto portfolio.

The KDE chart below shows the density distribution of returns for each strategy. 
 
![strategy_graph](https://github.com/kmg-regis/kmg_regis_msde_practicum_2/blob/main/images/strategy_graph.png)

## Results by Portfolio

 ![trader_style_graph](https://github.com/kmg-regis/kmg_regis_msde_practicum_2/blob/main/images/trader_style_graph.png) 
 ![trader_style_perf_table](https://github.com/kmg-regis/kmg_regis_msde_practicum_2/blob/main/images/trader_style_perf_table.png)
 
•	Solana (SOL) was the clear winner of this time period

   o	#2 Cutting Edge and #3 Diversified portfolios both had SOL exposure as well

•	S&P 500 portfolio performance highlighted as Traditional
   
   o	9.7% is a good performance for 14 months in an equity portfolio, but almost every other crypto portfolio beat it during this period (even the meme coins!) 

•	Over a longer period of time (5+ years), Bitcoin (BTC) would win, as it has shown most consistent growth

## Risks
The 14 months that these tests covered were an extremely good time period for the crypto market overall. However, in 2022 the market crashed hard, losing an estimated <b>~$2 trillion</b> in value. Many people’s entire life savings were wiped out due to the extreme losses and collapses triggered by this downswing.

The industry is also very prone to fraud, theft, scams, and general misinformation. FTX and Celsius Network are two examples of well-established, highly revered crypto exchanges that were revealed during the crash to be stealing billions of dollars in customers’ money. Terra was a well-established currency similar to Bitcoin and Ethereum, with high trading volume and relatively stable growth, which turned out to be a $40 billion pump-and-dump scheme. 

There are also many scams on the individual level. “Pig butchering” scams and fake crypto advisors have cost victims over $75 billion worldwide. 

Due to the nature of crypto trading, exchanges and accounts are always vulnerable to cyber-attacks from hackers. There is no regulatory or legal protective structure in place, nor is there a centralized institution to pursue stolen assets. Transactions and accounts are anonymous, so once asset theft occurs, there is little to no possibility of getting it back. 

## Conclusions
The extreme volatility leads to both opportunities and risks that don’t exist in classic securities trading. It is not an equivalent or a substitute for equities, but for a trader with a high risk appetite, it can be a valuable asset as a small percentage of a portfolio. Overall, I believe the term cryptocurrency is a misnomer since it is hard to use as currency or rely on to retain value. 

<u>Opportunities</u>

•	Extreme volatility leads to extreme performance (sometimes!)

•	Global access & markets never close

•	Speculation and diversification 

•	Innovation and disruption of traditional systems of power

<u>Risks</u>

•	Challenging to use as currency or liquidate

•	No investor protections

•	Cybersecurity issues

•	Industry is rife with fraud and scams

•	Legal & regulatory uncertainty

•	Transactions are complex; transaction fees and timing are unpredictable

## Future Possibilities
In a future version, this backtesting engine could be designed to take in data over a longer timeframe, continue adding newer data, and run tests regularly as the market changes. 
The Portfolio could also be designed to accept a custom balance of currencies and cash in order to track a specific configuration, reflecting real-life holdings.

The ability to predict future prices is limited due to the extreme volatility of the cryptocurrency market. 

## Resources
The backtesting engine design was adapted from [Zachary Raicik](https://medium.com/@raicik.zach/python-backtesting-a-beginners-guide-to-building-your-own-backtester-c31bddf05a59).

All data used belongs to [Binance.com](https://www.binance.com), [Coinbase.com](https://www.coinbase.com), and [Yahoofinance.com](https://www.yahoofinance.com).




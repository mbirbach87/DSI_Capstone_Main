# DSI_Capstone

The problem: Stock trading has existed for many decades. Whether it be quant funds or individuals, everyone is always looking for an edge. Each year many people/organizations try to beat a benchmark index known as the S&P 500. Many have tried to beat this and have failed. The question is could I build a successful model that could beat the benchmark index over time.

The goal: To take into account sentiment index. I initially wanted to to use a daily sentiment index in order to predict where the market would go the next day. I ran into some issues. This type of data is available, but is extremely proprietary. Funds aren't willing to just give this away for free. I tried to access this data through the Quandl API, but they charge about $750 to access this data. I then tried to download a large CSV from another website from their "free/sample" version, but the data was useless and essentially gibberish. The third option was to try to create my own sentiment index. If you look in the Stocktwits_API.ipynb file, you will see that I attempted to scrape tweets, but ran into another issue. They cap the limit at 30 tweets per request and you can only scrape the most recent 30 tweets. This wouldn't be enough to make meaningful observations. The other option was to try and scrape reddit, but also ran into scraping limitation. Ultimately, I settled on a weekly strategy that involves taking sentiment data from the S&P weekly AAI poll.

The data was taken using the quandl API. It is free to use. In order to access their API you will need to sign up for a free account and they will grant you an API code to use. From quandl.com: The AAII Investor Sentiment Survey measures the percentage of individual investors who are bullish, bearish, and neutral on the stock market for the next six months; individuals are polled from the ranks of the AAII membership on a weekly basis. Only one vote per member is accepted in each weekly voting period.

I interacted with their API which can be seen in the Quandl_API notebook. I then saved the data into a CSV so I would have an archive.

I also took into account VIX data:
CBOE Volatility Index, known by its ticker symbol VIX, is a popular measure of the stock market's expectation of volatility implied by S&P 500 index options, calculated and published by the Chicago Board Options Exchange (CBOE). It is colloquially referred to as the fear index or the fear gauge. The current VIX concept formulates a theoretical expectation of stock market volatility in the near future. The current VIX index value quotes the expected annualized change in the S&P 500 index over the following 30 days, as computed from options-based theory and current options-market data

Since I am setting up a weekly trading strategy I will be taking weekly VIX data from January 2010 up till October 2018. The data comes from yahoo finance and I will read in a CSV file.

The other data was taking the weekly S&P 500 weekly data from Yahoo Finance. I read in a csv.
Data cleaning and EDA was performed to clean all the data and make all the columns and rows match. The EDA can be seen in the EDA notebook.

From there it was time to make some models. My first instinct was to make a linear regression model. That failed miserably. From there I realized that this needed to be a classification problem, where a given the VIX and Sentiment data I attempted to predict if the next week would be up or down. Then the ultimate question was answered: Could my model beat the S&P 500. Finally I ran a simulation to see if one invested 10,000 what the overall return would be. To see the results, check out the models notebook.

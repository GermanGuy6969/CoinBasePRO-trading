# CrypFinder Bot 
## Version 1.55


## Summary: 
CrypFinder is a Coinbase Pro API trading bot that currently implements a basic momentum trading strategy and reverse momentum trading strategy in NodeJS using the Coinbase Pro API, as well as its own custom library for the endpoints that are not supported by the now deprecated Coinbase Pro NodeJS Library. Currently, Coinbase Pro limits the number of portfolios to five, this means that the bot can run up to four trading instances simultaneously per Coinbase Pro account. This bot can be modified to trade any product pairs available on Coinbase Pro, such as BTC-USD, ETH-USD, etc., but stablecoin (USDC to other coins) and crypto markets (coin to other coins) aren't currently tested, only USD markets (USD to coins). 

The momentum strategy will work as follows: The bot will start by getting the amount of USD available for the provided API key's profile (profile=portfolio on the coinbase pro website). If the amount is greater than zero, it will monitor the price changes of the chosen product using a peak/valley system; if the price changes by the specified delta, it will purchase a position. Then, it will monitor price changes until the delta condition and profit condition are met; after selling for a profit, it can deposit a cut of the profit to a different portfolio for saving. The reverse momentum trading strategy, is, as the name implies the reverse where it sells when the price goes up and buys when it goes down.

The bot features a number of variables at the top that can be configured to customize how it trades. This includes the deltas that specify an amount of price change that will trigger a buy/sell, the minimum acceptable profit from a trade, the name of currency to trade, the profile names, the deposit enable/disable flag, the deposit amount, and more. Of course, any of the code can be modified to customize it fully. This project is a great way to trade crypto on Coinbase Pro through their API.

## How to run the program:
1. Create a coinbase pro account. Install [CrypFinder](), open CrypFinder.exe
2. Setup your Coinbase Pro account portfolios (portfolios are also referred to as profiles). Each bot that runs needs it's own portfolio. The bot will take any available balance in the portfolio that it's tied to via the API key and start trading with it. Coinbase Pro gives you the default (Default Portfolio) to start with, but, you can add up to four more (5 is the max). Don't use a bot to trade in the default portfolio because that's where money transfers go by default; which, means the funds could get swept up by the bot before you can allocate them where you want. Create a new portfolio for each bot you want to run, for example you could create one called "BTC trader" that the bot trades bitcoin inside of. If you wish to use the feature that deposits all or a portion of profits into another portfolio to save it then by default those deposits will go to the default portfolio, but you have the option to create a different portfolio to use instead. Take note of the profile names you created as you will need them in steps 5 & 6.
3. Create the API key for the portfolio you want the bot to trade on, give it View/Trade/Transfer permissions and whitelist your public IP. [More info here](https://help.coinbase.com/en/pro/other-topics/api/how-do-i-create-an-api-key-for-coinbase-pro). 



## Momentum and reverse momentum trading strategy analyzer:
The analyzers are a way to run data against the bot strategy to see how well it performs. It takes in a .csv file with OHLC data. Carston Klein has already compiled a massive dataset that is perfect for this task and it's available for free on Kaggle [check it out](https://www.kaggle.com/tencars/392-crypto-currency-pairs-at-minute-resolution?select=ampusd.csv). After downloading the file for the coin data you want, just trim the .csv file to the length of time you want to test and run the analyzer with the configuration you want and it will generate a report showing how it did. He also wrote [this article](https://medium.com/coinmonks/how-to-get-historical-crypto-currency-data-954062d40d2d) on how to get similar data yourself.

## Helpful links:
[Coinbase Pro](https://pro.coinbase.com/trade/BTC-USD)

[Coinbase Pro API Docs](https://docs.pro.coinbase.com/#introduction)

[Coinbase Pro NodeJS Library](https://www.npmjs.com/package/coinbase-pro)

[Flow diagram of the momentum strategy, open it in Google draw.io for best results (May be outdated, but can help to give an idea of how the program works)](https://drive.google.com/file/d/1sMg7nWcuCDwHS5wdwHgoe5qqODO7UEFA/view?usp=sharing)

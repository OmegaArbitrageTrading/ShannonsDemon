---
layout: default
---
<p align="justify">
Welcome to the homepage of Shannon's Demon. The trading bot that grows the value of your crypto portfolio by repeatedly rebalancing your portfolio. For more information about the bot's trading strategy, please check: <a href="https://thepfengineer.com/2016/04/25/rebalancing-with-shannons-demon/">rebalancing-with-shannons-demon</a>. Get your bot running in less than 5 minutes. For now only Binance is supported.</p>
* * *
![shannonsdemon.exe](bot.png)
* * *
<p align="justify">
<i>How the bot works...</i> Let's start with a portfolio worth 1000 USD and trade BNB/USDT (<b>market</b>). Since we have to start with a perfectly balanced portfolio, we buy 500 USD worth of USDT (<b>quote_asset_qty</b>) and 500 USD worth of BNB (<b>base_asset_qty</b>). At a current price of of 20 BNBUSDT that is 25 BNB. This is also called the equilibrium price.
</p>
T0: 500.0 USDT + 25.00 BNB x 20.0 BNB/USDT = 1000.0 USDT.
<p align="justify">
At T1 the price decreases to 15.0 BNB/USDT and to be perfectly balanced again the bot buys 4.17 BNB in exchange for 62.5 USDT.
</p>
T1: 500.0 USDT + 25.00  BNB x 15.0 BNB/USDT = 875.0 USDT.<br>
T1: Rebalance: buy 4.17 BNB.<br>
T1: 437.5 USDT + 29.17 BNB x 15.0 BNB/USDT = 875.0 USDT.
<p align="justify">
At T2 the price increases to 20.0 BNB/USDT and to be perfectly balanced again the bot sells 3.65 BNB in exchange for 72.92 USDT.
</p>
T2: 437.50 USDT + 29.17 BNB x 20.0 BNB/USDT = 1020.8 USDT.<br>
T2: Rebalance: sell 3.65 BNB.<br>
T2: 510.42 USDT + 25.52 BNB x 20.0 BNB/USDT = 1020.8 USDT.
<p align="justify">
As you can see in the above example we have generated a small retrun of approximately 2%. Over time the bot generates many small returns which are immediately re-invested (similar to receiving compound interest, the 8th world wonder). This is also known as volatility harvesting and if there is plenty of something in the crypto space, it is volatility. 
</p>
<p align="justify">
The given example is a simplified explanation of how the bot works. Actually it starts with sending orders at the equilibrium price multiplied by <b>buy_percentage</b> and <b>sell_percentage</b>. With these parameters equal to 0.9 and 1.1 that would be orders with price of 18 and 22 BNB/USDT at time T0. After waiting <b>sleep_seconds_after_send_orders</b> seconds, the bot cancels all open orders, processes all new (trade id > <b>fromId</b>) trades that were send with this bot and finally waits another <b>sleep_seconds_after_cencel_orders</b> seconds. Every <b>rebalance_interval_sec</b> seconds instead of sending orders at fixed percentages, the bot sends special orders. These special orders rebalance at the current price given that it's more than 5% away from equilibrium.
</p>
* * *
![config.json](configjson.png)
* * *
<p align="justify">
<i>Prerequisites...</i> Download shannonsdemon.exe and config.json and put both files in the same folder. If you don't trust running an executable, which you shouldn't if you don't have some sort of dedicated system, you can also clone the github repository and run the python script. Open a new account on <a href="https://www.binance.com/nl/register?ref=R9NNDYS8">Binance.</a> Please use our link for a 20% discount in trading fees of which we receive half. Obviously you can also use an existing account. <a href="https://www.binance.com/en/support/articles/360002502072">Create api keys</a> and make sure to have trading option enabled and withdrawal option disabled. Fund your account, make sure you have the right quantities for every market you want to trade and set all parameters in the config.json file using for example <a href="https://code.visualstudio.com/">Visual Studio Code</a>.</p>
* * *
<p align="justify">
<i>How to start your bot...</i> It is very important that you always start the bot with <b>state</b> unequal to TRADE (e.g. TEST) to check if the orders that are about to be send make sense. We advise you to always start your bot following the steps below until you know what you are doing:
</p>
<p align="justify">
1. Set <b>state</b> equal to TEST in config file. Start your bot by double clicking the executable or by running the python script. Wait until you see [end processing trades] in the ui and stop the bot. If you received any error messages you need to solve the errors first and restart the bot until it runs error free. Now all new trades are processed and <b>fromId</b> is updated if necessary.
</p>
<p align="justify">
2. Now you can increase or decrease the <b>base_asset_qty</b> and <b>quote_asset_qty</b> but make sure that all markets are close to equilibrium. Re-start the bot with <b>state</b> still equal to TEST and check if DUMMY order prices for all markets make sense. The [b:] and [s:] percentage are 0% if in equilibrium. If too far from equilibrium an error is thrown that an order would hit the market and most of the time you have made a mistake in quantities. After checking all markets you can stop the bot.  
</p>
<p align="justify">
3. Change the <b>state</b> to TRADE and start your bot. After [end sending orders] you can sleep safe and get rich.
</p>
* * *
<i>Debugging...</i> Most error messages are self explanatory. However we want to mention all messages related to time sync. This means that the time of your computer is not in sync with the time of Binance's servers. Sync your system's clock in order to solve it. We have also seen that the time of the router needed to be synced. For all other error messages search <a href="https://github.com/binance-exchange/binance-official-api-docs/blob/master/rest-api.md">Binance rest-api documentation</a>. The bot uses Samm Chardy's <a href="https://python-binance.readthedocs.io/en/latest/">python-binance</a> library. You can look there also. Don't hesitate to contact us for any help.
* * *
Contact: <a href="mailto:OmegaArbitrageTrading@outlook.com"><b>OmegaArbitrageTrading@outlook.com</b></a> or <a href="https://discord.gg/mnkE4Xb"><b>https://discord.gg/mnkE4Xb</b>.</a>
* * *
Donate:

ETH:   0x13d55ca40ca3d008b7b0a0118d295f510410b60f

USDT:  0x13d55ca40ca3d008b7b0a0118d295f510410b60f

BTC:   1Fxyo5jfMxkDgGDjiAU9KE7svEG6Drriyv

LTC:   Lbqi2McxsrhM2NR3FtgiMiF2JxswFBsmMX
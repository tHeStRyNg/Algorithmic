=========  ALGORITHMIC RSI STORM =========

--- You can Get the EA on the following MQL5 link --> https://www.mql5.com/en/market/product/106056
--- FOR GAO - For the GAO - Genetic Algorithmic Optimized Setup file which you can load on EA config (.set config file), DM me, or pick up the link on YT video.

=========  DESCRIPTION  =========

The scope of this EA is to provide a decent Entry and Exit Strategy with an interesting approach of execution allowing total and daily DD to be targeted at given point in time so your DD isnt impacted. Cute for Prop Firms.
This algo was under GAO (Genetic Algorithm Optimization) and we are only using the best settings thus hardcoded on the EA) so the GAO is targeting only Wednesdays and on H1.
Just change the lot size to 1.9 to 10.0 lots cross all pairs (EURUSD,EURGBP,EURCAD,EURAUD,EURCHF,EURNZD,USDJPY,USDCAD,CADCHF,CADJPY,GBPNZD,GBPUSD,GBPCHF,GBPAUD,GBPCAD,GBPJPY,AUDCAD,AUDNZD,AUDCHF,AUDJPY,NZDUSD,NZDCAD,NZDCHF,NZDJPY)
If it opens a position and is impacting profit, (Hedge Exit Strategy) a counter pending order will be opened at twice as much lot size as the initial trade to counter that trade and exist still with the specified amount of profit.


ENTRY STRATEGY - RSI / MACD Correlation.

EXIT STRATEGY - TP, Trailing SL, Daily Profit Value Reached, Global Profit Value Reached, Hedge as a failsafe and Global Max DD, Daily Max DD failover auto trigger kill switch always to back all your equity in case of market crash just setup your max DD % and that will be the trigger point.

=========  EA INPUT SPECS  =========

========= TIMEFRAME  =========

- TIMEFRAME - M1 to H4 -  (default GAO value - H1)

We did GAO - Genetic Algorithm Optimization and came across the fact that on H1 its the best performance TF (timeframe) cross last 5 years but we give you the freedon and choose not to hardcoded it so you can have freedom of choice.



========= INSTRUMENTS CONFIGURATION ========

- SYMBOLS - EURUSD,EURGBP,EURCAD,EURAUD,EURCHF,EURNZD,USDJPY,USDCAD,CADCHF,CADJPY,GBPNZD,GBPUSD,GBPCHF,GBPAUD,GBPCAD,GBPJPY,AUDCAD,AUDNZD,AUDCHF,AUDJPY,NZDUSD,NZDCAD,NZDCHF,NZDJPY

(default GAO value - all the above)

You can use just 1, 3, or all of them as the EA will automatically map crosses between MACD and RSI values for you which is the main purpose of this EA as its humanly impossible for someone to keep a sharp eye on all pairs at same point in time this EA will do it for you and enter a position cross all pairs if conditions are triggered.



========= TP & SL CONFIGURATION ========

TP_SL_ENABLED - false || true ( default GAO value - false)



====== LOTS CONFIG =====

- LOTS - 0.01 || 5000 - (default GAO value - 1.9)

You can use any lot size based on your Balance, on GAO best output results were with 1.9 Lots but we did extensive manual testing cross last years on all pairs and works great from 1.9 and 10 lots.



====== HEDGE CONFIG =====

HEDGE_MULTIPLIER - 0.1 || 500.0 - (default GAO value - 2.0)

Hedge Multiplier is the multiplication factor that a hedge entry should use to hedge a trade and its based on the lot value of a trade that isnt going so well. example a trade is in DD and was opened at 0.05 lots, this setting will configure that the Hedge Multiplier will enter the trade at x2 (twice as much (default config) as the initial opened position being atempted to hedge out so will open a hedge at 0.10 lots.

HEDGE_DISTANCE - 1 || 500 - (default GAO value - 150) 

Hedge Distance is the distance in pips from the order start.



===== MAX DRAWDOWN KILL SWITCH CONFIG =====

MAX DRAWDOWN STOP (enabled if = true) - false || true - (default GAO value - false)

if true, enables the EA to constantly monitor your DD.

MAX DRAWDOWN TO STOP ALL TRADES AT % (% of total balance) - 0.1 || 100 (% of your total equity = balance - floating) - (default GAO value - 0.5)

If above is set to true this value provides the trigger to close all trades and stop trading until next day at midnight broker time 23:59 hrs, will resume if you dont take action at 00:00 broker time.



===== PROFIT CONFIG =====

AMOUNT MONEY YOU WANT TO CLOSE A TRADE - 1 || 500000 - (default GAO value - 500 for 1.9 lots and 1000 for 10 lots)

Value definition for closing a trade. Value in currency. Example, so you are using 5 lots and you want to close a trade at 5,000 as scenario 1 or you have 20 lots and you want achieve same 5,000 in a position so the second scenario will be more likely to produce a more probable result as its easier for a higher lot size to reach this value meaning 5 lots to reach 5,000 it isnt impossible but less probable and higher risk.

DEFINES MAX DAILY PROFIT - IF REACHED RESUMES NEXT DAY - 1 || 10000 - (default GAO value - 24000.0)
This value defines what you have set as your daily goal to stop trading at lets say that throughtout the day you had 1 win and 1 hedge breakeven totaling 1000 value which is 1.000 $ so if this is hit (value excludes comissions) it stops trading for the day and will resume at 00:00 broker time.

DEFINES MAX TOTAL PROFIT GOAL THEN STOPS IF REACHED - 1 || 500000 - (default GAO value - 20000.0)

If this value is reached then triggers an all stop and the bot wont trade anymore until configuration is checked. Means that the value that you setup here example, 20000 (20,000 $) was reached from the start of trading to now (does daily accumulation calculation to assess the global balance).

DEFINES MAX DAILY LOSS - IF REACHED IT STOPS AND RESUMES NEXT DAY - 1 || 50000 - (default GAO value - -2000.0)

If this value is recahed, it triggers an all stop for all trades and closes them all forcefully not to impact your daily max DD limits.



======== TIME CONFIGURATION ======== 

Time configuration defines what is the start of the trading day hour and the end of the trading day hour all these values are based on your broker time.

START HOUR - 00:00 || 23:59 - (default GAO value - 00:01)

END HOUR - 00:00 || 23:59 - (default GAO value - 23:59)

MONDAY - ENABLED TRUE/FALSE - true || false - (default GAO value - false)

TUESDAY - ENABLED TRUE/FALSE - true || false - (default GAO value - false)

WEDNESDAY - ENABLED TRUE/FALSE - true || false - (default GAO value - true)

THURSDAY - ENABLED TRUE/FALSE - true || false - (default GAO value - false)

FRIDAY - ENABLED TRUE/FALSE - true || false - (default GAO value - false)

SATURDAY - ENABLED TRUE/FALSE - true || false - (default GAO value - false)

SUNDAY - ENABLED TRUE/FALSE - true || false - (default GAO value - false)



======== MAX_PARALLEL_TRADES CONFIGURATION ======== 

Defines how many trades you can have in a given point in time open in parallel

MAX_ PARALLEL _TRADES_BUY - 1 || 50 - (default GAO value - 1)

MAX_ PARALLEL _TRADES_SELL - 1 || 50 - (default GAO value - 5)

TOTAL_MAX_ PARALLEL _TRADES - 1 || 50 - (default GAO value - 6)



NOTE: SUSTAINED RESULTS ARE BASED ON GAO (GENETIC ALGORITHMIC OPTIMIZED) CONFIG SETTINGS ACROSS THE LAST 5 YEARS OF DATA IN A OPTIMIZED AND TUNNED WAY, DOESN'T MEAN THAT YOU CANT USE YOUR OWN DEFINITION OF SETTINGS, THIS IS EXACTLY WHY WE LEFT OPENED THE INPUT POSSIBILITY SO YOU CAN HAVE A CHOICE, STILL, BARE IN MIND THAT GAO CONFIGURATION GREATLY INCREASES PROBABILITIES ON THE LONG RUN FOR INCREASED PROFICIENCY.

DM me if any, and wish you great time and profits using my algo.

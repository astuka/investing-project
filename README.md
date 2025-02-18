# investing-project
My investing portfolio, open-sourced.

# The Theory (Read this before you invest)

This algorithm follows three central tenets:
1. We, as market participants, cannot reasonably predict where a stock price will go.
2. Stocks that have had a winning streak in recent past are more likely -- but not not guaranteed -- to continue to win in the recent future.
3. A win is always better than a loss, no matter the magnitude. 

To make sure we follow these tenets, we apply the following rules to our algorithm:
1. ETFs Only: ]]]]
2. Volatility-adjusted EMA filtering: This assists the step 3 process by making sure we have ETFs that 1) have been winning recently, and 2) are performing well given their risk. The Kelly weighting system has a bias towards "sure things" like bonds, which is fantastic in times of recession but if we're in an economic boom we'd rather ride out something like tech stocks. This filtering makes sure we're doing exactly that.
3. Kelly portfolio weights: ]]]
4. ATR-optimized trailing stop: ]]]]

This new algorithm supports two things that my old one didn't: trailing stops and ]]]]

Whenever we can, we're using the 1-month or 21-day time schedule. This theory only really works on shorter time frames -- if your time horizon is longer, you're better off just going straight into the S&P 500. This cuts a lot of the S&P's losses though it will occassionally underperform its wins (except the beautiful occassions where a win is orchestrated by previously winning sectors, in which case you will far exceed the S&P).

# What it does

Given a universe of ETFs with positive measure of (21-day EMA/1-month Volatility):
1. Find normalized Kelly portfolio weights
2. Find ATR-optimized trailing stop
3. Export as CSV for easy trading
4. ???
5. Profit!

Repeat this once a week on Mondays. Use your buying/purchasing power!


# What to watch out for

If you are just dumping a universal list of ETFs and not pre-vetting the ETFs, you may come across scammy ETFs that pass the filters due to the fact that they win big and often. There are measures that should cut these ETFs (we kick any ETF that has a 21-day winning streak, aka "too good to be true" ETFs) but you should still vet anytime the algo asks you to buy a million shares of an ETF you do not recognize!

If this algorithm is functioning properly, it should do one of two things: in times of recession/high volatility, it should be investing you primarily in "sure things" such as ultra short US govt bonds. If it is a time of plenty, it should be helping you ride out on top-performing equities. If you get something far different than one of these two options, check to make sure you implemented correctly!

# How to use

1. Set up venv
2. Install requirements.txt
3. Run notebook


# TODO
- Weigh daily returns by most recent
- make a more "scientific" measure for the ATR multiplier


# UPDATES

2025/2/3 - Added a multiplier to the trailing stop so that ETFs wouldn't instantly sell within a few days
2025/2/18 - Fixed a bug that would end the kelly weighting if an all positive or all negative array was detected
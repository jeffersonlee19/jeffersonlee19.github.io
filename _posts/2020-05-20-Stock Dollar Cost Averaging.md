---
layout: post
title: Python code for Dollar Cost Averaging
---
_last edit: September 25, 2020_

Below is a python code to help you dollar cost average, specificly, the code will graphiaclly show your current average cost as well
as calculate your new average cost after a theoretical acquisition. You will need datetime, matplotlib, pandas, and colorama imported.

```python
from datetime import date
import matplotlib.pyplot as plt
from matplotlib import style
import pandas as pd
import pandas_datareader as web
from colorama import Fore, Back, Style

ticker = (input("Enter the ticker: "))
AVG = float(input("Enter your average cost for "+ticker+": "))
number = float(input("Enter how many current shares for "+ticker+": "))
check = True
while check == True:
    print("\n")
    from yahoo_fin import stock_info as si
    current = si.get_live_price(ticker)
    print("The current price of", ticker, "is $", '\033[1m',
          "{:.2f}".format(current), '\033[0m')
    print("Your average cost of", ticker, "is $", '\033[1m',
          "{:.2f}".format(AVG), '\033[0m')
    difference = abs(AVG-current)
    if current < AVG:
        print("You have an unrealized",
              Fore.RED, "loss", Fore.BLACK, "of $", '\033[1m',
              "{:.2f}".format(difference*number), '\033[0m')
    elif current > AVG:
        print("You have an unrealized", Fore.GREEN,
              "gain", Fore.BLACK, "of $", '\033[1m',
              "{:.2f}".format(difference*number), '\033[0m')
    else:
        print("You are breaking even")
    start = date(2020, 1, 1)
    end = date.today()
    df = web.get_data_yahoo(ticker, start, end)
    plot = df["Adj Close"].plot()
    plot.axhline(y=AVG)
    plt.show()

    addnoshares = float(input("How many shares are bought (enter 0 for exit): "))
    if addnoshares == 0:
        check = False
        print('\033[1m', "Saved and exited.", '\033[0m')
    else:
        addprice = float(input("At what price are they bought?: "))
        AVG = (number*AVG+addnoshares*addprice)/(number+addnoshares)
        number += addnoshares
        
```

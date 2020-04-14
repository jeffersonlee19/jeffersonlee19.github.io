---
layout: page
title: Trading
subtitle: Money to make money
---
Trading using TDAmeritrade through application thinkorswim.
  * Largest holding (as of April 13th 2020): __Apple__
  * 2019 calendar year: * 4.55% portfolio growth


*(edit 13 April 2020)
(kind of redundant now that most brokerages have free commissions...)

Python code of commission calculator on mac on a standalone application using py2app.

```python
import tkinter as tk
root = tk.Tk()
root.geometry("640x480")
root.config(bg='#778899')

### need a csv file called data to store data ###
file = open('data.csv', 'r')
old = file.readline()
def quick(n):
    """
    this function adds number 'n' to number of total trades and writes into csv file
    this bypasses the enter and submit function
    """
    final = int(n)+int(old)
    file = open('data.csv', 'w+')
    file.write(str(final))
    root.destroy()
def enter():
    """
    this function takes input number and returns it
    """
    n = entry_num.get()
    return(n)
def submit():
    """
    this function writes the csv file with the new number from enter function
    """
    n = enter()
    final = int(n)+int(old)
    file = open('data.csv', 'w+')
    file.write(str(final))
    root.destroy()
def cancel():
    root.destroy()

### title of program ###
label_top = tk.Label(root, text="all time total trades and commissions")
label_top.place(relx=.5, rely=0.05, anchor='center')
label_top.config(font=("Courier", 14),fg='black',bg='#778899')

label_trade = tk.Label(root, text=old + " trades")
label_trade.place(relx=.5, rely=0.14, anchor='center')
label_trade.config(font=("Courier", 16),fg='black',bg='#778899')

### change the 6.95 to cost per trade from your own brokerage ###
label_money = tk.Label(root, text="$"+ str(round(float(old)*6.95,2)))
label_money.place(relx=.5, rely=0.2, anchor='center')
label_money.config(font=("Courier", 25),fg='red',bg='#778899')

label_quick = tk.Label(root, text="quick add")
label_quick.place(relx=.5, rely=0.3, anchor='center')
label_quick.config(font=("Courier", 14),fg='black',bg='#778899')

### quickly adds n to the number of total trades (replace n with actual number)###
button_quick1 = tk.Button(root, text="n", command= lambda: quick(n))
button_quick1.place(relx=.4, rely=0.35, anchor='center')
button_quick1.config(font=("Courier", 18),fg='black',bg='#778899')

label_num = tk.Label(root, text="number of trades to add")
label_num.place(relx=.5, rely=0.58, anchor='center')
label_num.config(font=("Courier", 18),fg='black',bg='#778899')

### type to add to the number of total trades ###
entry_num = tk.Entry(root)
entry_num.place(relx=.5, rely=0.65, anchor='center')
entry_num.config(fg='black',bg='#778899')

### submit button ###
button_submit = tk.Button(root, text="submit", command=submit)
button_submit.place(relx=.5, rely=0.85, anchor='center')
button_submit.config(font=("Courier", 22),fg='black',bg='#778899')

### cancel and exit button ###
button_cancel = tk.Button(root, text="cancel", command=cancel)
button_cancel.place(relx=.5, rely=0.95, anchor='center')
button_cancel.config(font=("Courier", 16),fg='black',bg='#778899')

root.title("commission calculator")

root.mainloop()
file.close()
```

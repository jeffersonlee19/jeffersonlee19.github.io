---
layout: page
title: Trading
subtitle: Money to make money
---
Trading using TDAmeritrade.
  * Largest holding (as of August 4th 2019): __Boeing__

Python code of mac application of commission calculator

```python
import tkinter as tk
root = tk.Tk()
root.geometry("640x480")
root.config(bg='#778899')

### need a csv file called data to store data ###
file = open('data.csv', 'r')
num = file.readline()
def quick(n):
    """
    adds number 'n' to number of total trades and writes into csv file
    bypasses the enter and submit function
    """
    newnum = n
    final = int(newnum)+int(num)
    file = open('data.csv', 'w+')
    file.write(str(final))
    file.close
    root.destroy()
def enter():
    """
    takes input number and returns it
    """
    newnum = entry_num.get()
    return(newnum)
def submit():
    """
    writes the csv file with the new number from enter function
    """
    newnum = enter()
    final = int(newnum)+int(num)
    file = open('data.csv', 'w+')
    file.write(str(final))
    file.close
    root.destroy()
def cancel():
    root.destroy()

### title of program ###
label_top = tk.Label(root, text="all time total trades and commissions")
label_top.place(relx=.5, rely=0.05, anchor='center')
label_top.config(font=("Courier", 14),fg='black',bg='#778899')

label_trade = tk.Label(root, text=num + " trades")
label_trade.place(relx=.5, rely=0.14, anchor='center')
label_trade.config(font=("Courier", 16),fg='black',bg='#778899')

### change the 6.95 to cost per trade from your own brokerage ###
label_money = tk.Label(root, text="$"+ str(round(float(num)*6.95,2)))
label_money.place(relx=.5, rely=0.2, anchor='center')
label_money.config(font=("Courier", 25),fg='red',bg='#778899')

label_quick = tk.Label(root, text="quick add")
label_quick.place(relx=.5, rely=0.3, anchor='center')
label_quick.config(font=("Courier", 14),fg='black',bg='#778899')

### quickly adds n to the number of total trades (replace n with number) ###
button_quick1 = tk.Button(root, text="1", command= lambda: quick(n))
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

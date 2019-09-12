---
layout: page
title: Engineering
subtitle: and some coding
---
Learning basics of SolidWorks.
Currently self learning Python, familiarizing in Tkinter and Py2app.

Creating standalone application from python on Mac.
Thanks to marinamele.com for great tutorial.

open terminal and cd to folder of python file and install py2app
```unix
cd Desktop/code/fees
```
```unix
pip install -U py2app
```

make setup.py with py2app. replace ### with file name
```unix
py2applet --make-setup ###.py
```

create app. if using older version of python, try python instead of python3
```unix
python3 setup.py py2app -A                         
```

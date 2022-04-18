Calculator using eval function:

```
import re

while True:
  expression = input("Input expression: ")
  expression = expression.replace('x', "*")
  expression = expression.replace('÷', "/")

  expression = re.sub(r"(?<=\d)\(", "*(", expression)
  expression = re.sub(r"\)(?<=\d)", ")*", expression)
  expression = expression.replace(")(", ")*(")
  
  try:
    print("Answer:", eval(expression))
  except:
    print("Invalid expression, try again.")
```

Calculator using eval function + tkinter gui:

```
import re
import tkinter as tk
import tkinter.ttk as ttk
from math import *

root = tk.Tk()
root.title("soocc's simple calculator")

style = ttk.Style()
style.theme_use("alt")

canvas = tk.Canvas(root, width = 400, height = 300)
canvas.pack()

def on_enter(event):
  evaluate()

entry = tk.Entry(root)
entry.config(font=('helvetica', 30))
entry.bind('<Return>', on_enter)
canvas.create_window(200, 140, window = entry)

output = tk.Label(root, text = "")
output.config(font = ('helvetica', 30))

def evaluate():
  if entry.get() == "":
    pass
  else:
    # Format input to be compatible with eval function
    input = entry.get()
    input = input.replace('x', "*")
    input = input.replace('÷', "/")
    input = input.replace('^', "**")
    input = input.replace(")(", ")*(")
    input = re.sub(r"(?<=\d)\(", "*(", input)
    input = re.sub(r"\)(?<=\d)", ")*", input)

    try:
      output["text"] = eval(input)
    except:
      output["text"] = "Calculation Error"
    canvas.create_window(200, 90, window = output)

def clear():
  entry.delete(0, "end")
  output["text"] = ""

evalbutton = tk.Button(text = 'Evaluate', command = evaluate)
evalbutton.config(font = ('helvetica', 30))
canvas.create_window(200, 200, window = evalbutton)

clearbutton = tk.Button(text = 'Clear', command = clear)
clearbutton.config(font = ('helvetica', 30))
canvas.create_window(200, 250, window = clearbutton)

root.mainloop()
```

Enjoy :)

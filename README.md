# pythonproject1-
cu project 
import tkinter as tk
import math

def click(event):
    text = event.widget.cget("text")
    if text == "=":
        try:
            result = eval(screen.get())
            screen.delete(0, tk.END)
            screen.insert(tk.END, str(result))
        except:
            screen.delete(0, tk.END)
            screen.insert(tk.END, "Error")
    elif text == "C":
        screen.delete(0, tk.END)
    elif text == "π":
        screen.insert(tk.END, str(math.pi))
    elif text == "e":
        screen.insert(tk.END, str(math.e))
    elif text == "√":
        try:
            result = math.sqrt(float(screen.get()))
            screen.delete(0, tk.END)
            screen.insert(tk.END, str(result))
        except:
            screen.delete(0, tk.END)
            screen.insert(tk.END, "Error")
    elif text == "^":
        screen.insert(tk.END, "**")
    elif text in ["sin", "cos", "tan", "log"]:
        try:
            val = float(screen.get())
            if text == "sin":
                result = math.sin(math.radians(val))
            elif text == "cos":
                result = math.cos(math.radians(val))
            elif text == "tan":
                result = math.tan(math.radians(val))
            elif text == "log":
                result = math.log10(val)
            screen.delete(0, tk.END)
            screen.insert(tk.END, str(result))
        except:
            screen.delete(0, tk.END)
            screen.insert(tk.END, "Error")
    else:
        screen.insert(tk.END, text)

root = tk.Tk()
root.title("Scientific Calculator")

screen = tk.Entry(root, font="Arial 20", bd=10, relief=tk.SUNKEN, justify="right")
screen.grid(row=0, column=0, columnspan=6, padx=10, pady=10)

buttons = [
    ["7", "8", "9", "/", "C", "π"],
    ["4", "5", "6", "*", "(", "e"],
    ["1", "2", "3", "-", ")", "^"],
    ["0", ".", "+", "=", "√", "log"],
    ["sin", "cos", "tan"]
]

for i, row in enumerate(buttons):
    for j, btn_text in enumerate(row):
        btn = tk.Button(root, text=btn_text, font="Arial 18", width=5, height=2)
        btn.grid(row=i+1, column=j, padx=5, pady=5)
        btn.bind("<Button-1>", click)

root.mainloop()


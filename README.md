# calculator_app.py
import tkinter as tk

def click(event):
    global expression
    expression += str(event.widget.cget("text"))
    input_text.set(expression)

def clear():
    global expression
    expression = ""
    input_text.set("")

def evaluate():
    global expression
    try:
        result = str(eval(expression))
        input_text.set(result)
        expression = result
    except:
        input_text.set("Error")
        expression = ""

# Main window
root = tk.Tk()
root.title("Calculator")
root.geometry("300x400")
root.resizable(False, False)

expression = ""
input_text = tk.StringVar()

# Input field
entry = tk.Entry(root, textvar=input_text, font=("Arial", 20), bd=10, relief="sunken", justify="right")
entry.pack(fill="both", ipadx=8, pady=10)

# Button layout
buttons = [
    ["7", "8", "9", "/"],
    ["4", "5", "6", "*"],
    ["1", "2", "3", "-"],
    ["0", ".", "=", "+"],
]

frame = tk.Frame(root)
frame.pack()

for row in buttons:
    row_frame = tk.Frame(frame)
    row_frame.pack(side="top", expand=True, fill="both")
    for char in row:
        b = tk.Button(row_frame, text=char, font=("Arial", 18), width=5, height=2)
        b.pack(side="left", expand=True, fill="both")
        if char == "=":
            b.config(command=evaluate)
        else:
            b.bind("<Button-1>", click)

# Clear button
clear_btn = tk.Button(root, text="Clear", font=("Arial", 18), command=clear)
clear_btn.pack(fill="both")

root.mainloop()
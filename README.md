import tkinter as tk

def click(event):
    global screen
    text = event.widget.cget("text")
    if text == "=":
        try:
            result = eval(screen.get())
            screen.set(result)
        except Exception as e:
            screen.set("Error")
    elif text == "C":
        screen.set("")
    else:
        screen.set(screen.get() + text)

root = tk.Tk()
root.title("Calculator N*Bom")
root.geometry("450x450")

label = tk.Label(master=root, text=('เครื่องคิดเลขของน้องบอม'))
screen = tk.StringVar()
screen.set("")
entry = tk.Entry(root, textvar=screen, font="Arial 20 bold", justify="right")
entry.pack(fill=tk.BOTH, ipadx=8, pady=10, padx=10)

button_frame = tk.Frame(root)
button_frame.pack()

buttons = [
    "7", "8", "9", "/",
    "4", "5", "6", "*",
    "1", "2", "3", "-",
    "C", "0", "=", "+"
]

row, col = 0, 0
for button in buttons:
    btn = tk.Button(button_frame, text=button, font="Arial 18 bold", relief=tk.RIDGE, height=2, width=4)
    btn.grid(row=row, column=col, padx=5, pady=5)
    btn.bind("<Button-1>", click)
    col += 1
    if col > 3:
        col = 0
        row += 1

root.mainloop()


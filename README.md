import tkinter as tk

def show_output():
    number = int(number_input.get())

    if number == 0:
        output_label.configure(text='ยังไงก็ได้ 0 ว้ายๆ')
        return

    output = ''
    for i in range(1,13):
        output += str(number) + 'x' + str(i)
        output += '=' + str(number*i) + '\n'
    
    output_label.configure(text=output)

window = tk.Tk()
window.title('เครื่องคิดเลข N*Bom')
window.minsize(width=400 , height=400)

title_label = tk.Label(master=window , text='สูตรคูณแม่ที่. . .')
title_label.pack(pady=15)

number_input = tk.Entry(master=window , width=15)
number_input.pack(pady=10)

button = tk.Button(master=window , text='Namely' , command=show_output , width=15)
button.pack()

output_label = tk.Label(master=window)
output_label.pack(pady = 10)

window.mainloop()

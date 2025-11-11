# Python-1
Keyboard
import tkinter as tk

def on_key_press(char):
    entry.insert(tk.END, char)

def on_space():
    entry.insert(tk.END, ' ')

def on_backspace():
    current = entry.get()
    entry.delete(0, tk.END)
    entry.insert(0, current[:-1])

root = tk.Tk()
root.title("On-screen Keyboard")

entry = tk.Entry(root, width=50)
entry.grid(row=0, column=0, columnspan=12)

keys = [
    ['Q', 'W', 'E', 'R', 'T', 'Y', 'U', 'I', 'O', 'P'],
    ['A', 'S', 'D', 'F', 'G', 'H', 'J', 'K', 'L'],
    ['Z', 'X', 'C', 'V', 'B', 'N', 'M']
]

for row_idx, row_keys in enumerate(keys, start=1):
    for col_idx, key in enumerate(row_keys):
        btn = tk.Button(root, text=key, width=5, command=lambda k=key: on_key_press(k))
        btn.grid(row=row_idx, column=col_idx)

space_btn = tk.Button(root, text='Space', width=30, command=on_space)
space_btn.grid(row=4, column=0, columnspan=6)

backspace_btn = tk.Button(root, text='Backspace', width=12, command=on_backspace)
backspace_btn.grid(row=4, column=6, columnspan=4)

root.mainloop()

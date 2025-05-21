Source Code.
import tkinter as tk
from tkinter import filedialog

def open_file():
    file = filedialog.askopenfilename(filetypes=[("Text Files", "*.txt")])
    if file:
        with open(file, "r") as f:
            text_area.delete("1.0", tk.END)
            text_area.insert(tk.END, f.read())

def save_file():
    file = filedialog.asksaveasfilename(defaultextension=".txt",
                                        filetypes=[("Text Files", "*.txt")])
    if file:
        with open(file, "w") as f:
            f.write(text_area.get("1.0", tk.END))

# Set up GUI
root = tk.Tk()
root.title("ExaEditor Lite")

text_area = tk.Text(root, wrap="word")
text_area.pack(expand=True, fill="both")

menu_bar = tk.Menu(root)
file_menu = tk.Menu(menu_bar, tearoff=0)
file_menu.add_command(label="Open", command=open_file)
file_menu.add_command(label="Save", command=save_file)
menu_bar.add_cascade(label="File", menu=file_menu)

root.config(menu=menu_bar)
root.mainloop()

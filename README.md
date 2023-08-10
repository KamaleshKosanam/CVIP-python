import tkinter as tk
from datetime import datetime
def calculate_age():
    birth_date = entry_birth_date.get()
    try:
        birth_date = datetime.strptime(birth_date, '%Y-%m-%d')
        current_date = datetime.now()
        age = current_date.year - birth_date.year - ((current_date.month, current_date.day) < (birth_date.month, birth_date.day))
        label_result.config(text=f"Your age is: {age} years")
    except ValueError:
        label_result.config(text="Please enter a valid date (YYYY-MM-DD)")
root = tk.Tk()
root.title("Age Calculator")
label_birth_date = tk.Label(root, text="Enter your birthdate (YYYY-MM-DD):")
label_birth_date.pack(pady=10)
entry_birth_date = tk.Entry(root)
entry_birth_date.pack(pady=5)
calculate_button = tk.Button(root, text="Calculate Age", command=calculate_age)
calculate_button.pack(pady=10)
label_result = tk.Label(root, text="")
label_result.pack()
root.mainloop()

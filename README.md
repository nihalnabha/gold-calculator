# gold-calculator
import tkinter as tk
from tkinter import messagebox
import datetime

def calculate_and_display():
    try:
        # Get the input values as floats
        gold_24k_rate = float(gold_24k_entry.get())
        silver_per_gram = float(silver_entry.get())
        
        # Calculate other values
        gold_rate_22k = gold_24k_rate / 1.03
        gold_916_hallmark = gold_rate_22k * 0.928
        gold_buy_back_22k = gold_916_hallmark - 220
        
        # Update the result label with formatted information
        result_label.config(
            text=f"Mysore recommend board rate\n"
                 f"-----------------------------\n"
                 f"Today's Date: {datetime.date.today().strftime('%Y-%m-%d')}\n"
                 f"Today is: {datetime.date.today().strftime('%A')}\n"
                 f"Gold 916 hallmark (22K): {gold_916_hallmark:.2f}\n"
                 f"Silver: {silver_per_gram:.2f} per gram\n"
                 f"Gold buy back 22K: {gold_buy_back_22k:.2f}\n"
                 f"Gold 24K: {gold_24k_rate:.2f}\n"
                 f"Gold 22K: {gold_rate_22k:.2f}"
        )
    except ValueError:
        # Display an error message if input is not valid
        messagebox.showerror("Error", "Invalid input. Please enter valid numbers.")

# Create the main application window
root = tk.Tk()
root.title("Gold Rate Calculator")

# Create and place GUI components
gold_24k_label = tk.Label(root, text="Gold 24K rate (Including GST):")
gold_24k_label.pack()

gold_24k_entry = tk.Entry(root)
gold_24k_entry.pack()

silver_label = tk.Label(root, text="Silver rate per gram:")
silver_label.pack()

silver_entry = tk.Entry(root)
silver_entry.pack()

calculate_button = tk.Button(root, text="Calculate", command=calculate_and_display)
calculate_button.pack()

result_label = tk.Label(root, text="Results will be shown here.", font=("Helvetica", 12))
result_label.pack()

# Start the main event loop
root.mainloop()

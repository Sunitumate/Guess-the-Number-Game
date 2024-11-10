# Guess-the-Number-Game
import random
import tkinter as tk
from tkinter import messagebox

# Function to handle game logic
def check_guess():
    try:
        user_guess = int(guess_entry.get())
        if user_guess < number_to_guess:
            messagebox.showinfo("Result", "Too Low! Try again.")
        elif user_guess > number_to_guess:
            messagebox.showinfo("Result", "Too High! Try again.")
        else:
            messagebox.showinfo("Result", "Congratulations! You guessed it!")
            reset_game()  # Reset after a correct guess
    except ValueError:
        messagebox.showerror("Error", "Please enter a valid number!")

# Function to reset the game
def reset_game():
    global number_to_guess
    number_to_guess = random.randint(1, 100)
    guess_entry.delete(0, tk.END)

# Initialize the main window
root = tk.Tk()
root.title("Guess the Number Game")
root.geometry("400x300")

# Add a label
label = tk.Label(root, text="Guess a number between 1 and 100", font=("Arial", 14))
label.pack(pady=20)

# Add an entry field for the user's guess
guess_entry = tk.Entry(root, font=("Arial", 14), width=10)
guess_entry.pack(pady=10)

# Add a button to submit the guess
submit_button = tk.Button(root, text="Check Guess", font=("Arial", 14), command=check_guess)
submit_button.pack(pady=20)

# Start the game with a random number
number_to_guess = random.randint(1, 100)

# Run the main event loop
root.mainloop()

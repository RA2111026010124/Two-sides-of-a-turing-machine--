

import tkinter as tk

class TuringMachineGUI:
    def __init__(self, root):
        self.root = root
        self.root.title("Two-Way Turing Machine for String Reversal and Palindrome Check")

        self.tape = ["_"] * 30  # Initialize a tape with 30 cells
        self.head_position = 15  # Start in the middle of the tape

        self.label = tk.Label(root, text="Enter a string:")
        self.label.pack()

        self.string_entry = tk.Entry(root)
        self.string_entry.pack()

        self.reverse_button = tk.Button(root, text="Reverse and Check Palindrome", command=self.reverse_and_check_palindrome)
        self.reverse_button.pack()

        self.output_label = tk.Label(root, text="")
        self.output_label.pack()

    def reverse_and_check_palindrome(self):
        input_string = self.string_entry.get()

        # Initialize the tape with the input string
        self.tape = list(input_string) + ["_"] * 15  # Add 15 blank cells for padding
        self.head_position = len(input_string) - 1

        # Simulate reversing the string
        reversed_string = ""
        while self.head_position >= 0:
            reversed_string += self.tape[self.head_position]
            self.head_position -= 1

        # Check if the input string is a palindrome
        is_palindrome = input_string == reversed_string

        # Update the output label
        if is_palindrome:
            self.output_label.config(text=f"Reversed string: {reversed_string}\nIt's a palindrome!")
        else:
            self.output_label.config(text=f"Reversed string: {reversed_string}\nIt's not a palindrome!")

if __name__ == "__main__":
    root = tk.Tk()
    app = TuringMachineGUI(root)
    root.mainloop()
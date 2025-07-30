import tkinter as tk

# Color palette inspired by Android Material Design
BG_COLOR = "#121212"
DISPLAY_COLOR = "#1E1E1E"
BTN_COLOR = "#2E7D32"
BTN_TEXT_COLOR = "white"
OPERATOR_COLOR = "#039BE5"
CLEAR_COLOR = "#D32F2F"
EQUAL_COLOR = "#388E3C"

FONT = ("Segoe UI", 20)

class Calculator(tk.Tk):
    def __init__(self):
        super().__init__()
        self.title("Colorful Calculator")
        self.configure(bg=BG_COLOR)
        self.geometry("350x500")
        self.resizable(False, False)

        self.expression = ""
        self.create_widgets()

    def create_widgets(self):
        self.display = tk.Entry(self, font=FONT, bg=DISPLAY_COLOR, fg="white",
                                bd=0, justify="right", insertbackground="white")
        self.display.pack(expand=True, fill="both", ipadx=8, ipady=25)

        btns_frame = tk.Frame(self, bg=BG_COLOR)
        btns_frame.pack(expand=True, fill="both")

        # Button layout
        buttons = [
            ["C", "←", "%", "/"],
            ["7", "8", "9", "*"],
            ["4", "5", "6", "-"],
            ["1", "2", "3", "+"],
            ["0", ".", "=", ""]
        ]

        for row in buttons:
            btn_row = tk.Frame(btns_frame, bg=BG_COLOR)
            btn_row.pack(expand=True, fill="both")
            for char in row:
                if char:
                    self.create_button(btn_row, char)

    def create_button(self, parent, char):
        btn = tk.Button(parent, text=char, font=FONT,
                        fg=BTN_TEXT_COLOR, bd=0, highlightthickness=0,
                        command=lambda: self.on_button_click(char))

        # Color rules
        if char == "C":
            btn.configure(bg=CLEAR_COLOR)
        elif char == "=":
            btn.configure(bg=EQUAL_COLOR)
        elif char in ["/", "*", "-", "+", "%"]:
            btn.configure(bg=OPERATOR_COLOR)
        else:
            btn.configure(bg=BTN_COLOR)

        btn.pack(side="left", expand=True, fill="both", padx=1, pady=1)

    def on_button_click(self, char):
        if char == "C":
            self.expression = ""
        elif char == "←":
            self.expression = self.expression[:-1]
        elif char == "=":
            try:
                self.expression = str(eval(self.expression))
            except Exception:
                self.expression = "Error"
        else:
            self.expression += char
        self.update_display()

    def update_display(self):
        self.display.delete(0, tk.END)
        self.display.insert(tk.END, self.expression)

if __name__ == "__main__":
    app = Calculator()
    app.mainloop()

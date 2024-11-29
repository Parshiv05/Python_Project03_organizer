# Simple Calculator Application Documentation

## Overview
This is a **Simple Calculator Application** implemented using the **Tkinter** library in Python. The application has a user-friendly graphical interface for basic arithmetic operations, including addition, subtraction, multiplication, and division. The application also has a "Clear" button that clears the calculations.

---

## Features
1. **Basic Arithmetic Operations**: Supports:
   - Addition (`+`)
   - Subtraction (`-`)
   - Multiplication (`*`)
- Division (`/`)
2. **Clear Functionality**: Clears the current input and resets the calculator.
3. **Error Handling**: Displays "Error" for invalid expressions.
4. **Responsive Buttons**: Interactive buttons for input and evaluation.

---

## Requirements
- **Python 3.x** installed on the system.
- **Tkinter**, which is included in most Python distributions.

---

## Workflow
1. **Setup**: A Tkinter window is created and the interface configured.
2. **Input**: Numbers and operators are input via interactive buttons.
3. **Evaluation**: The entered expression is evaluated using Python's `eval()` function.
4. **Error Handling**: Invalid expressions or errors (e.g., division by zero) are managed gracefully.
5. **Output**: The result is displayed in the input field.

---

## Code Explanation

### 1. Importing Libraries
```python
import tkinter as tk
```
- The **Tkinter** library is used to create the GUI for the calculator.

---

### 2. Defining the `click()` Function
```python
def click(event):
    text = event.widget.cget("text")
if text == "=":
        try:
            result = eval(entry.get())
            entry.delete(0, tk.END)
            entry.insert(tk.END, str(result))
        except Exception:
entry.delete(0, tk.END)
            entry.insert(tk.END, "Error")
    elif text == "C":
        entry.delete(0, tk.END)
    else:
        entry.insert(tk.END, text)
```

#### Functionality:
- **Retrieve Button Text**:
- Stores the text of the button clicked by `event.widget.cget("text")`.
- **Evaluate Expression (=)**:
  - The `eval()` function evaluates the mathematical expression in the input field.
  - Errors in invalid expressions are trapped by a `try-except` block, which shows "Error".
- **Clear Input (C)**:
  - Deletes all text in the input field with `entry.delete(0, tk.
Appends text of button to input area with `entry.insert()`.

------------------------------------------------

### 3. GUI Setup
#### MainWindow
```python
root = tk.Tk()
root.title("Simple Calculator")
```
A Tkinter root window is established and titled "Simple Calculator".

#### Entry Widget
```python
entry = tk.Entry(root, width=16, font=('Arial', 24), borderwidth=2, relief="solid")
entry.grid(row=0, column=0, columnspan=4)
```
**Purpose:** The input and display window for expressions and results.
- Attributes
  - width = 16: Sets width of visible entry field.
- `font=('Arial', 24)`: Set font and size.
  - `borderwidth=2` and `relief="solid"`: Draw a border around the entry widget.
- Takes up all four columns in the grid by using `columnspan=4`.

#### Button Layout
```python
buttons = [
    '7', '8', '9', '/',
    '4', '5', '6', '*',
    '1', '2', '3', '-',
    'C', '0', '=', '+'
]

row_val = 1
col_val = 0

for button in buttons:
    b = tk.Button(root, text=button, font=('Arial', 18), width=4)
    b.grid(row=row_val, column=col_val)
    b.bind("<Button-1>", click)
    col_val += 1
    if col_val > 3:
        col_val = 0
        row_val += 1
- Every button has been given the same styling `font=('Arial', 18)` and `width=4`.
- **Grid Positioning**:
  - Buttons have been positioned in a 4x4 grid using `grid()` where `row_val` and `col_val` are tracking where the buttons are.
  - Whenever the row is filled up `col_val > 3`, the column gets reset, and the row value increments.
- **Event Binding**:
  - `click()` has been bound to button clicks by using `.bind("<Button-1>", click)`

### 4. Running the Application
```
root.mainloop()
```
The `mainloop()` method begins the Tkinter event loop, displaying the window and keeping it responsive.

-----

## Running the Application
1. Save the script as a `.py` file (for example, `simple_calculator.py`).
2. Run the file:
   ```
   python simple_calculator.py
   ```
3. Use the calculator by clicking buttons to enter numbers and operators. Click `=` to compute the answer or `C` to erase the input.

---

## Sample Usage
1. Start the application.
2. Click buttons to type a mathematical expression:
  - Sample: `7 + 3`.
3. Click `=` to display the answer (`10`).
4. Click `C` to clear the calculator.

---

## Sample Button Arrangement

| **7** | **8** | **9** | **/** |
|-------|-------|-------|-------|
| **4** | **5** | **6** | **\\*** |
| **1** | **2** | **3** | **-** |
| **C** | **0** | **=** | **+** |

---

## Enhancements
1. **Input Using Keyboard**
   Permitting input of expressions directly through the input field using the keyboard
2. **Additional Functions**
   Square roots, percent, and exponentiation
3. **Error Messages** :
- Display elaborate error messages, like "Division by zero" or "Invalid input".
4. **Theme Configuration**:
   Allow the user to toggle between light and dark themes for enhanced usability.
5. **Memory Functions**:
   Add memory buttons to store and recall previous results, for example, "M+" and "MR".
The **Simple Calculator Application** is a straightforward application for performing simple arithmetic. It has a clean design and a responsive interface that is both functional and extendable. This is an example of a foundational application for GUI programming in Python using **Tkinter**.

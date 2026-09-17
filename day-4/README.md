# Expense Tracking System - Day 4 Assignment

**India Data Research Academy (IDRA) - Python Mini Project**

**Student Name:** Patel Harshilkumar Rajubhai
**Project:** Day 4 - Expense Tracking System
**Deliverable:** `IDRA DAY 4.ipynb`

---

## Assignment Statement

> Create a menu driven Expense Tracker Application in Python that stores expense records in a CSV file. Each expense should include the Date, Category, Amount, and an optional Note. The program should allow users to add new expenses, view all recorded expenses with the total amount spent, and display a category wise spending summary. Use functions, exception handling, and file handling to organize your code, ensuring that invalid input is handled gracefully and all expense data is saved and retrieved correctly from the CSV file.

---

## What This Program Does

A simple menu driven Expense Tracker that:

1. **Adds** a new expense (Date, Category, Amount, optional Note).
2. **Views** all expenses with the **total amount spent**.
3. Shows a **category-wise spending summary**.
4. Saves everything to `expenses.csv`, so records stay saved even after the program closes.

The whole idea is beginner friendly: one small function for one small job, with print messages at every step so the output is easy to follow.

---

## Requirement Checklist

| Assignment Requirement | Where It Is Done |
|---|---|
| Menu driven application | `while True` menu loop (add / view / summary / exit) |
| Store expense records in a CSV file | `save()` writes to `expenses.csv` |
| Date, Category, Amount, optional Note | `add()` collects all 4 values |
| View all recorded expenses + total amount | `view()` |
| Category-wise spending summary | `summary()` |
| Use functions | `load()`, `save()`, `add()`, `view()`, `summary()` |
| Exception handling | `try/except ValueError` for amount, `FileNotFoundError` for missing file |
| Invalid input handled gracefully | Wrong amount, negative amount, and wrong menu choice are all caught |
| Data saved and retrieved correctly | `load()` at start, `save()` after every add |

---

## How To Run

### Option 1 - Inside Jupyter / Colab

1. Open `IDRA DAY 4.ipynb`.
2. Run each cell from top to bottom.
3. Cells 1-5 define the functions. **Cell 6 (Test drive)** runs everything with sample data and shows the printed output. **Cell 7** is the real menu program.

> Note: the menu cell (section 7) waits for typing with `input()`, so inside Jupyter it is easier to run the program in a terminal instead.

### Option 2 - As a normal Python program

Copy all the function cells plus the menu loop into a file named `expense_tracker.py` and run:

```
python expense_tracker.py
```

---

## Code Walkthrough (one step at a time)

### 1. Import and empty list

```python
import csv

expenses = []
```

`csv` helps us read/write files. `expenses` is one list that holds every record like `[date, category, amount, note]`.

### 2. Load and save (file handling)

```python
def load():
    try:
        expenses.clear()
        with open("expenses.csv") as f:
            for row in csv.reader(f):
                if len(row) == 4 and row[0] != "Date":
                    expenses.append(row)
        print("Loaded", len(expenses), "expense record(s) from expenses.csv")
    except FileNotFoundError:
        print("No file found - starting a fresh list")
```

- `load()` brings old records back when the program starts. If the file does not exist yet, `FileNotFoundError` is caught and we just start empty - no crash.
- `save()` writes the header row and every expense back with `csv.writer`, so data is never lost.

### 3. Add a new expense

```python
def add():
    date = input("Enter date (dd/mm/yyyy): ")
    cat = input("Enter category (food, travel, rent, etc.): ")

    try:
        amt = float(input("Enter amount: "))
        if amt < 0:
            print("Amount cannot be negative. Please try again.")
            return
    except ValueError:
        print("Invalid amount. Please type a number.")
        return

    note = input("Enter note (optional): ")

    expenses.append([date, cat, amt, note])
    save()
    print("Expense added:", date, "|", cat, "|", amt, "|", note)
```

The amount is validated. Typing letters or a negative number gives a friendly message instead of crashing. After adding, `save()` writes straight to the CSV.

### 4. View expenses with total

```python
def view():
    if not expenses:
        print("No expenses yet. Add one first.")
        return

    total = 0
    print("Date       | Category | Amount | Note")
    print("-------------------------------------")
    for e in expenses:
        print(e[0], "|", e[1], "|", e[2], "|", e[3])
        total = total + float(e[2])

    print("-------------------------------------")
    print("Total amount spent:", total)
```

Prints every expense as a neat table, then adds up all amounts and prints the grand total.

### 5. Category-wise summary

```python
def summary():
    if not expenses:
        print("No expenses yet. Add one first.")
        return

    d = {}
    for e in expenses:
        cat = e[1]
        if cat not in d:
            d[cat] = 0
        d[cat] = d[cat] + float(e[2])

    print("Category-wise summary:")
    for cat in d:
        print(cat, "->", d[cat])
```

Groups spending by category with a dictionary and prints the total for each one, for example `food -> 550.0`.

### 6. Test drive (sample output)

The notebook runs the functions on 3 sample expenses so you can see every requirement working:

```
Added 3 sample expenses.
Saved all 3 expense(s) to expenses.csv

=== 1. View all expenses with the total amount spent ===
Date       | Category | Amount | Note
-------------------------------------
14/01/2026 | food | 200 | samosa
15/01/2026 | travel | 120 | auto
16/01/2026 | food | 350 | dinner
-------------------------------------
Total amount spent: 670.0

=== 2. Category-wise spending summary ===
Category-wise summary:
food -> 550.0
travel -> 120.0
```

### 7. Main menu loop (the actual assignment)

```python
load()

while True:
    print()
    print("1. Add expense   2. View expenses   3. Summary   4. Exit")
    ch = input("Enter your choice: ")

    if ch == "1":
        add()
    elif ch == "2":
        view()
    elif ch == "3":
        summary()
    elif ch == "4":
        print("Goodbye! Thanks for using the Expense Tracker.")
        break
    else:
        print("Invalid choice. Please pick 1, 2, 3 or 4.")
```

Keeps showing the menu until the user picks **4**. Any other input prints "Invalid choice" and the loop continues safely.

Example session:

```
1. Add expense   2. View expenses   3. Summary   4. Exit
Enter your choice: 1
Enter date (dd/mm/yyyy): 17/01/2026
Enter category (food, travel, rent, etc.): rent
Enter amount: 5000
Enter note (optional): monthly rent
Saved all 4 expense(s) to expenses.csv
Expense added: 17/01/2026 | rent | 5000.0 | monthly rent

Enter your choice: 2
Date       | Category | Amount | Note
-------------------------------------
14/01/2026 | food | 200 | samosa
15/01/2026 | travel | 120 | auto
16/01/2026 | food | 350 | dinner
17/01/2026 | rent | 5000.0 | monthly rent
-------------------------------------
Total amount spent: 5670.0

Enter your choice: 4
Goodbye! Thanks for using the Expense Tracker.
```

---

## Files In This Folder

| File | Purpose |
|---|---|
| `IDRA DAY 4.ipynb` | The main notebook with explanation, functions and demo |
| `expenses.csv` | Created automatically when the notebook runs (stores the records) |
| `README.md` | This explanation |
| `LICENSE` | MIT license |

---

## What We Used

| Concept | Where |
|---|---|
| `csv` module | Read and write `expenses.csv` |
| List | `expenses = []` stores all records |
| Dictionary | Category totals in `summary()` |
| Functions | `load()`, `save()`, `add()`, `view()`, `summary()` |
| Loops | `while True` menu, `for` loop over expenses |
| `if/elif/else` | Menu routing, amount validation |
| Exception handling | `ValueError` and `FileNotFoundError` |

---

## Conclusion

The Day 4 Expense Tracker meets every part of the assignment: it is menu driven, saves data to a CSV file, adds expenses with Date/Category/Amount/Note, shows all expenses with the total amount spent, and gives a category-wise summary. It uses functions for clean structure, exception handling for safe input, and file handling so records are never lost. Simple to read, simple to run, and ready to grow into a bigger personal finance tool.

---

## Author

**Student Name:** Patel Harshilkumar Rajubhai
**Topic:** Expense Tracking System
**Project:** Day 4

---

## License

This project is open-source and released under the **MIT License**. See the [LICENSE](LICENSE) file for details.
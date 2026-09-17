# 🎓 Student Grade Management System - Python Mini-Project (OOP)

**Student Name:** Patel Harshilkumar Rajubhai
**Project Track:** Day 5 Python Mini-Project using Object-Oriented Programming (OOP)
**Deliverable:** `IDRA DAY 5.ipynb` (Menu-driven OOP Application)

---

## 📌 Executive Summary

This project is a **menu-driven Student Grade Management System** built with **Object-Oriented Programming (OOP)** in Python.

The application models each student as a `Student` class object and stores a list of these objects in memory. Records are **persisted to a CSV file** so data survives between runs. The program supports adding a student, viewing all students with total marks and grades, searching for a student by ID, and finding the top-performing student.

The project deliberately applies all the concepts learned in Week 1 — **variables, conditionals, loops, functions, lists, sets, dictionaries, exception handling, file handling (CSV), and OOP (classes, objects, constructors, methods)** — while handling invalid user input gracefully.

---

## 🗂️ Assignment Problem Statement

> Create a menu driven Python Mini Project using Object-Oriented Programming (OOP) by choosing any one of the following applications: Library Management System, Student Grade Management System, ATM Simulation, Movie Ticket Booking System, Hospital Management System, Restaurant Ordering System, Shopping Cart System, Quiz Application, Hotel Room Booking System, or Employee Payroll System. Design your project using appropriate classes, objects, constructors, and methods, while applying all the concepts learned throughout Week 1, including variables, conditional statements, loops, functions, data structures (lists, tuples, sets, dictionaries), exception handling, and file handling (TXT/CSV) wherever applicable. Your application should be menu driven, well structured, and capable of handling invalid user input gracefully.

**Chosen Application:** Student Grade Management System

---

## 🛠️ OOP & Python Concepts Used

| Concept | Where It Is Used |
|---------|------------------|
| Class | `Student` class defines the blueprint of a student record |
| Object | `Student(sid, name, marks)` objects stored in the `students` list |
| Constructor | `__init__(self, sid, name, marks)` initializes each student |
| Methods | `total()` (sums marks) and `grade()` (returns A/B/C based on average) |
| List | `students = []` holds all `Student` objects |
| Dictionary | `marks = {"Math": m, "Science": m, "English": m}` stores subject-marks |
| Set | `{"Math", "Science", "English"}` used to loop over subjects |
| Tuple | `best = (name, total)` to hold the top student pair |
| Loops | `while True` menu loop, `for` loops over students |
| Conditionals | `if`/`elif` menu routing, `if` validation of marks range |
| Functions | `load()`, `save()`, `add()`, `view()`, `search()`, `top()` |
| Exception Handling | `try/except FileNotFoundError` and `ValueError` |
| File Handling | `csv.reader` / `csv.writer` to read & write `students.csv` |

---

## ⚙️ How the Program Works

### 1. The `Student` Class

```python
class Student:
    def __init__(self, sid, name, marks):
        self.sid = sid
        self.name = name
        self.marks = marks

    def total(self):
        return sum(self.marks.values())

    def grade(self):
        avg = self.total() / 3
        if avg >= 90:
            return "A"
        elif avg >= 75:
            return "B"
        else:
            return "C"
```

- The constructor stores **ID, Name, and a dictionary of subject marks**.
- `total()` returns the sum of Math + Science + English marks.
- `grade()` computes the average and maps it to a letter grade:
  - **A** → 90 or above
  - **B** → 75 to 89
  - **C** → below 75

### 2. CSV File Handling

```python
def load():
    try:
        with open("students.csv") as f:
            for row in csv.reader(f):
                if len(row) == 5 and row[0] != "ID":
                    marks = {"Math": int(row[2]), "Science": int(row[3]), "English": int(row[4])}
                    students.append(Student(row[0], row[1], marks))
    except FileNotFoundError:
        pass

def save():
    with open("students.csv", "w", newline="") as f:
        w = csv.writer(f)
        w.writerow(["ID", "Name", "Math", "Science", "English"])
        for s in students:
            w.writerow([s.sid, s.name, s.marks["Math"], s.marks["Science"], s.marks["English"]])
```

- `save()` writes every student object to `students.csv` (with a header row) after each add.
- `load()` reads the CSV back into `Student` objects at startup and **silently ignores a missing file** using `FileNotFoundError` — so the program runs clean on the first launch.

### 3. Menu Options

| Choice | Action |
|--------|--------|
| 1 | Add Student (ID, Name, Math/Science/English marks) |
| 2 | View All Students (ID, Name, Total, Grade) |
| 3 | Search Student (by ID) |
| 4 | Top Student (highest total marks) |
| 5 | Exit |

### 4. Available Functions

| Function | What It Does |
|----------|--------------|
| `add()` | Reads ID, Name and marks for 3 subjects with validation, creates a `Student` object, appends it, then calls `save()` |
| `view()` | Prints a table of ID, Name, Total and Grade for every student |
| `search()` | Finds and prints a student's full record by ID |
| `top()` | Scans all students and prints the one with the highest total marks |
| `load()` / `save()` | CSV persistence between program runs |

### 5. Flow of Execution

1. `load()` reads any existing `students.csv` into memory.
2. The `while True` loop keeps showing the menu until the user exits.
3. The choice is routed through `if`/`elif` (with an `else` for invalid choices).
4. Every successful add automatically saves back to CSV.
5. Choosing **5** prints "Goodbye!" and breaks the loop.

---

## 🔍 Code Walkthrough

### Add Function with Validation

```python
def add():
    sid = input("Enter ID: ")
    name = input("Enter name: ")
    marks = {}
    subjects = {"Math", "Science", "English"}
    for sub in sorted(subjects):
        try:
            m = int(input("Enter " + sub + " marks (0-100): "))
            if m < 0 or m > 100:
                print("Marks must be 0-100!")
                return
        except ValueError:
            print("Invalid marks! Enter a number.")
            return
        marks[sub] = m
    students.append(Student(sid, name, marks))
    save()
    print("Student added!")
```
- Uses a **set** of subjects, `sorted()` for consistent order.
- **`ValueError`** is caught when the user types a non-number — the program reports the mistake and returns gracefully instead of crashing.
- Marks outside **0–100** are rejected before the record is created.

### View Function

```python
def view():
    if not students:
        print("No students!")
        return
    print("ID | Name | Total | Grade")
    for s in students:
        print(s.sid, "|", s.name, "|", s.total(), "|", s.grade())
```
- Guards against an empty list and prints each student's computed total and grade.

### Top Student Function

```python
def top():
    if not students:
        print("No students!")
        return
    best = (students[0].name, students[0].total())
    for s in students:
        if s.total() > best[1]:
            best = (s.name, s.total())
    print("Top student:", best[0], "with", best[1], "marks")
```
- Uses a **tuple** to track the current highest (name, total) pair.

---

## 💡 Example Usage

```
1. Add  2. View  3. Search  4. Top  5. Exit
Enter choice: 1
Enter ID: 201
Enter name: Aarav
Enter Math marks (0-100): 95
Enter Science marks (0-100): 88
Enter English marks (0-100): 80
Student added!

1. Add  2. View  3. Search  4. Top  5. Exit
Enter choice: 2
ID | Name | Total | Grade
201 | Aarav | 263 | B
```

If a non-number is entered for marks, the program prints `Invalid marks! Enter a number.` and safely returns to the menu instead of crashing.

---

## ✅ Why This Design Is Good

- **True OOP design** — students are objects with behaviour (`total()`, `grade()`), not just raw data.
- **Data persists** — records are saved to and loaded from CSV, making the system practical rather than demo-only.
- **Robust input handling** — invalid numbers and out-of-range marks are caught and reported politely.
- **Graceful startup** — a missing CSV file does not crash the program.
- **Clean structure** — each operation is a small, focused function; the menu is trivial to extend (e.g., average, pass/fail, delete, update).
- **Applies Week 1 concepts** — variables, conditionals, loops, functions, lists, tuples, sets, dictionaries, exceptions, file handling, and OOP all appear in one small program.

---

## 🎯 Conclusion

The Day 5 Student Grade Management System fulfils the mini-project requirements by using **Object-Oriented Programming** to build a menu-driven, well-structured application. The `Student` class with its constructor and methods cleanly encapsulates record data and behaviour, CSV file handling provides persistence, and exception handling keeps the program stable even with bad user input.

The project demonstrates a complete grasp of Week 1 Python fundamentals and OOP, and its clean design makes it easy to extend into a fuller grade-management system later.

---

## 👤 Author Information

**Student Name:** Patel Harshilkumar Rajubhai
**Topic:** Student Grade Management System (Python Mini-Project)
**Project:** Day 5

---

## 📜 License

This project is open-source and released under the **MIT License**. See the [LICENSE](LICENSE) file for details.
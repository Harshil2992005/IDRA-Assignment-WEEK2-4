# 🎓 Student Management System - Python Assignment

**Student Name:** Patel Harshilkumar Rajubhai
**Project Track:** Day 3 Student Management System
**Deliverable:** `IDRA DAY 3.ipynb` (Menu-driven Python Program)

---

## 📌 Executive Summary

This project builds a complete **menu-driven Student Management System** in Python that stores student records using a **list of dictionaries**.

The program lets the user perform all the basic CRUD (Create, Read, Update, Delete) operations on student records:

- **Add** new students (ID, Name, Age, Course, Marks)
- **View** all student records
- **Search** for a student by ID or name
- **Update** existing student details
- **Delete** student records

The program is organised using appropriate **data structures (list + dictionaries)**, **loops**, **conditional statements**, and **functions**, making it easy to use, extend, and understand — exactly as required by the assignment.

---

## 🗂️ Assignment Problem Statement

> Create a menu driven Student Management System in Python that stores student records using a list of dictionaries. Each student record should include ID, Name, Age, Course, and Marks. The program should allow users to add new students, view all student records, search for a student by ID or name, update existing student details, and delete student records. Use appropriate data structures, loops, conditional statements, and functions to organize your program, ensuring that it is easy to use and well structured.

---

## 🛠️ Tools & Features Used

| Concept | Where It Is Used |
|---------|------------------|
| List | `students = []` — stores all student records |
| Dictionary | Each student is stored `{"ID", "Name", "Age", "Course", "Marks"}` |
| Functions | `add_student()`, `view_students()`, `search_student()`, `update_student()`, `delete_student()` |
| Loops | `while True` menu loop, `for s in students` iteration |
| Conditionals | `if`/`elif` chain for menu choice, `if` checks for record matching |
| Input / Output | `input()` for data entry, `print()` for menu and results |

---

## ⚙️ How the Program Works

### 1. Data Storage
- A global list `students = []` holds all records.
- Each record is a **dictionary** with 5 keys: `ID`, `Name`, `Age`, `Course`, `Marks`.

### 2. Menu System
The program runs an infinite `while True` loop that keeps showing this menu until the user exits:

| Choice | Action |
|--------|--------|
| 1 | Add Student |
| 2 | View Students |
| 3 | Search Student |
| 4 | Update Student |
| 5 | Delete Student |
| 6 | Exit |

### 3. Available Functions

| Function | What It Does |
|----------|--------------|
| `add_student()` | Takes ID, Name, Age, Course, Marks from the user and appends a new dictionary to the list |
| `view_students()` | Loops through the list and prints every student record |
| `search_student()` | Asks for an ID or Name and prints the matching record(s) |
| `update_student()` | Finds a student by ID and allows editing Name, Age, Course, and Marks |
| `delete_student()` | Finds a student by ID and removes the record from the list |

### 4. Flow of Execution
1. User is shown the menu (1–6).
2. Choice is read with `input()`.
3. `if`/`elif` statements route to the correct function.
4. The process repeats until the user selects **6 (Exit)**, which breaks the loop.

---

## 🔍 Code Walkthrough

```python
students = []   # list of dictionaries to store records

def add_student():
    sid = input("Enter ID: ")
    name = input("Enter Name: ")
    age = input("Enter Age: ")
    course = input("Enter Course: ")
    marks = input("Enter Marks: ")
    student = {"ID": sid, "Name": name, "Age": age, "Course": course, "Marks": marks}
    students.append(student)
    print("Student added!")
```
- The `add_student()` function collects the 5 fields from the user, wraps them into a dictionary, and appends it to the global `students` list.

```python
def view_students():
    for s in students:
        print(s)
```
- `view_students()` iterates over the list and prints each dictionary as a row.

```python
def search_student():
    key = input("Enter ID or Name: ")
    for s in students:
        if s["Name"] == key or s["ID"] == key:
            print(s)
```
- `search_student()` accepts either an ID or a Name and prints every record that matches either field.

```python
def update_student():
    sid = input("Enter ID: ")
    for s in students:
        if s["ID"] == sid:
            s["Name"] = input("New Name: ")
            s["Age"] = input("New Age: ")
            s["Course"] = input("New Course: ")
            s["Marks"] = input("New Marks: ")
            print("Updated!")
```
- `update_student()` locates the student by ID and overwrites the fields with new inputs.

```python
def delete_student():
    sid = input("Enter ID: ")
    for s in students:
        if s["ID"] == sid:
            students.remove(s)
            print("Deleted!")
```
- `delete_student()` finds the student by ID and removes that dictionary from the list using `remove()`.

```python
while True:
    print("1 Add  2 View  3 Search  4 Update  5 Delete  6 Exit")
    ch = input("Enter choice: ")
    if ch == "1":
        add_student()
    elif ch == "2":
        view_students()
    elif ch == "3":
        search_student()
    elif ch == "4":
        update_student()
    elif ch == "5":
        delete_student()
    elif ch == "6":
        break
```
- The main loop repeatedly displays the menu, reads the user's choice, and routes it to the matching function. Choosing **6** executes `break` and ends the program.

---

## 💡 Example Usage

```
1 Add  2 View  3 Search  4 Update  5 Delete  6 Exit
Enter choice: 1
Enter ID: 101
Enter Name: Riya
Enter Age: 20
Enter Course: BCA
Enter Marks: 92
Student added!

1 Add  2 View  3 Search  4 Update  5 Delete  6 Exit
Enter choice: 2
{'ID': '101', 'Name': 'Riya', 'Age': '20', 'Course': 'BCA', 'Marks': '92'}
```

---

## ✅ Why This Design Is Good

- **Simple & readable** — each operation is a small, focused function.
- **Real-world data model** — a list of dictionaries is the natural way to store structured records in Python.
- **Menu driven** — friendly for non-technical users; no need to memorise commands.
- **Extendable** — new features (e.g., marks statistics, grade calculation, save to file) can be added by writing one more function and one more menu option.
- **Covers all CRUD operations** — Add, View, Search, Update, Delete are all present.

---

## 🎯 Conclusion

The Day 3 Student Management System successfully fulfils the assignment requirements. It stores records as a list of dictionaries, provides a self-explanatory menu, and supports adding, viewing, searching, updating, and deleting students through well-organised functions using loops, conditionals, and basic data structures.

The program is a clean illustration of core Python fundamentals and demonstrates good program structure that can easily grow into a larger record-management application (e.g., a file-backed or database version).

---

## 👤 Author Information

**Student Name:** Patel Harshilkumar Rajubhai
**Topic:** Student Management System
**Project:** Day 3

---

## 📜 License

This project is open-source and released under the **MIT License**. See the [LICENSE](LICENSE) file for details.
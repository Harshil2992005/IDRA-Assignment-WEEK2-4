# 🧮 Simple Arithmetic Calculator — Day 1

**Student Name:** Patel Harshilkumar Rajubhai  
**Project Track:** Day 1 — Python Basics & Arithmetic Operations  
**Deliverable:** `IDRA DAY 1.ipynb` (Interactive Jupyter Notebook)

---

## 📌 Assignment Overview

Create a Python program that accepts **two numbers** from the user and performs **all the basic arithmetic operations** on them. The program displays the results of:

| Operation | Symbol |
|-----------|--------|
| Addition | `+` |
| Subtraction | `-` |
| Multiplication | `*` |
| Division | `/` |
| Floor Division | `//` |
| Modulus | `%` |
| Exponentiation | `**` |

---

## 🧰 What This Notebook Demonstrates

1. **User Input Handling** — `input()` with clear prompts
2. **Type Conversion** — `int()` to convert string input to numeric
3. **Arithmetic Operators** — all 7 operators applied on the two numbers
4. **Conditional Logic** — `if / else` guard to handle division by zero safely
5. **Formatted Output** — readable, clearly-labelled printed results

---

## 🚦 Edge-Case Handling

If the **second number is zero**, division, floor division, and modulus cannot be performed (undefined / division by zero). The program guards this with a conditional check and prints a clear message instead of crashing:

```
Division of two numbers cannot be performed due to second number as zero.
Floor Division of two numbers cannot be performed due to second number as zero.
Modulo of two numbers cannot be performed due to second number as zero.
```

Exponentiation (`num1 ** num2`) still runs — e.g. `0 ** 0` evaluates to `1` in Python.

---

## ▶️ How to Run

```bash
jupyter notebook "IDRA DAY 1.ipynb"
```

or run the code directly:

```python
num1 = int(input("\n enter a first number for an Arithmatic Opeartaion:"))
num2 = int(input("\n enter a second number for an Arithmatic Opeartaion:"))

print("\n sum of two numbers:", num1 + num2)
print("\n minus of two numbers:", num1 - num2)
print("\n multiplication of two numbers:", num1 * num2)

if num2 == 0:
    print("\n Divison of two numbers cannot be performed due to second number as zero")
    print("\n Floor Divison of two numbers cannot be performed due to second number as zero")
    print("\n Modulo of two numbers cannot be performed due to second number as zero")
else:
    print("\n Division of two numbers:", num1 / num2)
    print("\n Floor Division of two numbers:", num1 // num2)
    print("\n Modulo of two numbers:", num1 % num2)

print("\n exponentiation of two numbers:", num1 ** num2)
```

---

## 🖥️ Sample Output

```
 enter a first number for an Arithmatic Opeartaion: 12
 enter a second number for an Arithmatic Opeartaion: 0

 sum of two numbers: 12
 minus of two numbers: 12
 multiplication of two numbers: 0
 Division of two numbers cannot be performed due to second number as zero
 Floor Division of two numbers cannot be performed due to second number as zero
 Modulo of two numbers cannot be performed due to second number as zero
 exponentiation of two numbers: 1
```

---

## 🎯 Learning Outcomes

- Understand how to capture and convert user input in Python
- Apply all arithmetic operators correctly
- Use conditional statements to handle runtime edge cases
- Write clean, readable, and well-formatted output

---

## 📂 Folder Contents

```
IDRA DAY 1/
├── IDRA DAY 1.ipynb   # Interactive notebook
├── LICENSE            # MIT License
└── README.md          # This file
```

---

## 👤 Author Information

* **Student Name:** Patel Harshilkumar Rajubhai  
* **Academic Focus:** Information Technology & Data Analytics  
* **Topic:** Python Fundamentals — Arithmetic Operations

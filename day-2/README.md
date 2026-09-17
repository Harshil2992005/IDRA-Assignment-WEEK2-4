# 🎲 Number Guessing Game — Day 2

**Student Name:** Patel Harshilkumar Rajubhai  
**Project Track:** Day 2 — Python Loops, Conditions & Random Module  
**Deliverable:** `IDRA DAY 2.ipynb` (Interactive Jupyter Notebook)

---

## 📌 Assignment Overview

Create a **Number Guessing Game** in Python that generates a random number within a specified range (1–50) and asks the user to guess it. The program gives feedback whether the guess is **too high**, **too low**, or **correct**, while limiting the player to a fixed number of attempts (10).

---

## 🧰 What This Notebook Demonstrates

1. **Random Number Generation** — `random.randint(lower, upper)` picks a secret number between 1 and 50
2. **Loops** — a `for` loop runs the game for a fixed number of attempts (10)
3. **Conditional Statements** — `if / elif / else` compares the guess to the secret number
4. **User Input** — `input()` + `int()` to capture and convert the player's guess
5. **Win / Loss Messages** — clear success or failure message at the end of the game

---

## 🎮 How the Game Works

| Step | What happens |
|------|--------------|
| 1 | The program picks a secret number from 1 to 50 |
| 2 | The player enters a guess |
| 3 | The program says **"Too high"**, **"Too low"**, or **"Correct"** |
| 4 | Steps 2–3 repeat until the player guesses right or uses all 10 attempts |
| 5 | A final message shows **"You're a winner!"** or the limit was reached |

---

## ▶️ How to Run

```bash
jupyter notebook "IDRA DAY 2.ipynb"
```

Run the code cell and start guessing numbers!

---

## 🎬 Sample Session

```
 enter a number from your side! 20
 it's too high!!
 enter a number from your side! 10
 it's too low!!
 enter a number from your side! 15
 you guessed Correct no!
 your winnerr!!!
```

---

## 🎯 Learning Outcomes

- Generate random numbers using the `random` module (`random.randint`)
- Use `for` loops to control a fixed number of attempts
- Apply `if / elif / else` to compare values and give feedback
- Convert user input with `int()` and handle a simple game loop
- Write a clear, user-friendly program

---

## 📂 Folder Contents

```
IDRA DAY 2/
├── IDRA DAY 2.ipynb   # Interactive notebook (game code)
├── LICENSE            # MIT License
└── README.md          # This file
```

---

## 👤 Author Information

* **Student Name:** Patel Harshilkumar Rajubhai  
* **Academic Focus:** Information Technology & Data Analytics  
* **Topic:** Python Fundamentals — Number Guessing Game

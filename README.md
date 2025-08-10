# 🧩 Sudoku Solver — Backtracking

**Project:** Sudoku Using Backtracking  
**Authors:**  Archi Jaiswal [RA2211003030369]  
**Guide:** Mrs. Ambuja Kulshreshtha  
**Institute:** SRM Institute of Science & Technology — Delhi NCR Campus (Modinagar)  
**Date:** April 2024

---

## 📌 Overview
This project implements a Sudoku solver using the **backtracking** algorithm. The solver fills a 9×9 Sudoku grid so that each row, column, and 3×3 subgrid contains digits 1–9 exactly once. The implementation can be used as a baseline for comparing brute-force, human-strategy, or optimized solvers.

---

## 🔧 Features
- Classic 9×9 Sudoku solver using backtracking.
- `isSafe` checks row, column and 3×3 box constraints.
- Console input support and sample puzzle included.
- Easy to extend with heuristics (MRV, forward-checking, etc.).

---

## 🛠 Tech Stack / Requirements
- Language: **Java** (JDK 8+ recommended)
- IDE: Eclipse / IntelliJ / VS Code / OnlineGDB / Replit
- No external libraries required.

---

## 💻 How to run (quick)
1. Create a file `SudokuSolver.java` and paste the Java code from this repo.
2. Run locally:
   ```bash
   javac SudokuSolver.java
   java SudokuSolver

# Data Structures Internal Activity 3 – Question 2

## Student details

- **Name:** Dipakshi Chanchlani
- **PRN:** 202501100057
- **Subject:** Data Structures
- **Project:** Build-in-the-Open Lab Project – Hash Table with Recorded Development Log
- **Language:** C++

## Project description

This menu-free program inserts the personalized Mango Varieties dataset into a
hash table. It uses the division method and linear probing, reports every
collision during insertion, rejects duplicate and negative keys, and displays
the final table and insertion statistics.

## Personalization and configuration

- Last four PRN digits, `S`: 57
- Scenario: Mango Varieties
- Dataset formula: `v[i] = (S + 13*i) % 100`, for `i = 0..19`
- Table size: 29, retained from the existing project (no assignment PDF was
  present in the workspace)
- Hash function: `h(key) = key % 29`
- Collision resolution: Linear probing

The dataset is:

```text
57, 70, 83, 96, 9, 22, 35, 48, 61, 74,
87, 0, 13, 26, 39, 52, 65, 78, 91, 4
```

## Features

- Inserts all 20 dataset values and shows each initial hash index, collision,
  and final insertion position.
- Counts each occupied slot encountered during probing as one collision.
- Rejects a duplicate key and a negative key without changing the table.
- Displays all 29 indexes, occupied values, and empty positions.
- Reports the input and successful insertion counts, collisions, occupied and
  empty positions, and load factor.

## Compile and run

From the project directory, compile with a C++17 compiler:

```sh
g++ -std=c++17 -Wall -Wextra -pedantic IA3_Q2.cpp -o IA3_Q2
```

On Windows, run:

```powershell
.\IA3_Q2.exe
```

The program is deterministic and requires no interactive input.

## Output image

The captured output for the personalized dataset is available at
[screenshots/program_output.png](screenshots/program_output.png).

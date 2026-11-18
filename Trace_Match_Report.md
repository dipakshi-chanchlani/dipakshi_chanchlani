# Trace-Match Report

**Student:** Dipakshi Chanchlani
**PRN:** 202501100057
**Subject:** Data Structures
**Project:** Internal Activity 3 – Question 2

## Configuration

- Scenario: Mango Varieties
- Personalization seed: `S = 57`
- Dataset formula: `v[i] = (S + 13*i) % 100`, for `i = 0..19`
- Table size: 29, retained from the existing project; no assignment PDF was
  present in the workspace
- Hash function: `h(key) = key % 29`
- Collision resolution: linear probing, wrapping from index 28 to index 0
- Dataset: `57, 70, 83, 96, 9, 22, 35, 48, 61, 74, 87, 0, 13, 26, 39, 52, 65, 78, 91, 4`

## Independent hand prediction

Starting with 29 empty slots, each key was placed at its remainder modulo 29;
when that slot was occupied, the next slots were checked in order. The
collisions move `9` from 9 to 10, `0` from 0 to 1, `39` from 10 to 11, and
`4` from 4 to 5. This independent trace predicts:

| Index | Expected value | Index | Expected value | Index | Expected value |
|---:|:---|---:|:---|---:|:---|
| 0 | 87 | 10 | 9 | 20 | 78 |
| 1 | 0 | 11 | 39 | 21 | Empty |
| 2 | Empty | 12 | 70 | 22 | 22 |
| 3 | 61 | 13 | 13 | 23 | 52 |
| 4 | 91 | 14 | Empty | 24 | Empty |
| 5 | 4 | 15 | Empty | 25 | 83 |
| 6 | 35 | 16 | 74 | 26 | 26 |
| 7 | 65 | 17 | Empty | 27 | Empty |
| 8 | Empty | 18 | Empty | 28 | 57 |
| 9 | 96 | 19 | 48 |  |  |

Expected counts: 20 inserted keys, 4 collisions, 20 occupied positions, 9 empty
positions, and load factor `20 / 29 = 0.689655...`, displayed to four decimal
places as `0.6897`.

## Actual program output

Captured by compiling and running `IA3_Q2.cpp` with the required C++17 warning
flags. Whitespace in the code block is normalized for readability (the dataset
line's trailing space and the table's tab separators are omitted):

```text
DATA STRUCTURES IA 3 - QUESTION 2
Student: Dipakshi Chanchlani
PRN: 202501100057
Scenario: Mango Varieties
Personalization: v[i] = (57 + 13*i) % 100
Hash Function: h(key) = key % 29
Collision Handling: Linear Probing
Table Size: 29

Personalized Dataset:
57 70 83 96 9 22 35 48 61 74 87 0 13 26 39 52 65 78 91 4

========== INSERTION PROCESS ==========
Inserting 57 | Hash index = 28 | Inserted at index 28
Inserting 70 | Hash index = 12 | Inserted at index 12
Inserting 83 | Hash index = 25 | Inserted at index 25
Inserting 96 | Hash index = 9 | Inserted at index 9
Inserting 9 | Hash index = 9 | Collision at index 9 | Inserted at index 10
Inserting 22 | Hash index = 22 | Inserted at index 22
Inserting 35 | Hash index = 6 | Inserted at index 6
Inserting 48 | Hash index = 19 | Inserted at index 19
Inserting 61 | Hash index = 3 | Inserted at index 3
Inserting 74 | Hash index = 16 | Inserted at index 16
Inserting 87 | Hash index = 0 | Inserted at index 0
Inserting 0 | Hash index = 0 | Collision at index 0 | Inserted at index 1
Inserting 13 | Hash index = 13 | Inserted at index 13
Inserting 26 | Hash index = 26 | Inserted at index 26
Inserting 39 | Hash index = 10 | Collision at index 10 | Inserted at index 11
Inserting 52 | Hash index = 23 | Inserted at index 23
Inserting 65 | Hash index = 7 | Inserted at index 7
Inserting 78 | Hash index = 20 | Inserted at index 20
Inserting 91 | Hash index = 4 | Inserted at index 4
Inserting 4 | Hash index = 4 | Collision at index 4 | Inserted at index 5

========== DUPLICATE KEY TEST ==========
Duplicate key 57 ignored.

========== INVALID KEY TEST ==========
Invalid key -10. Negative values are not allowed.

========== INSERTION SUMMARY ==========
Total input values: 20
Successfully inserted: 20
Total collisions: 4
Occupied positions: 20
Empty positions: 9
Load factor: 0.6897

========== FINAL HASH TABLE ==========
Index   Value
0       87
1       0
2       Empty
3       61
4       91
5       4
6       35
7       65
8       Empty
9       96
10      9
11      39
12      70
13      13
14      Empty
15      Empty
16      74
17      Empty
18      Empty
19      48
20      78
21      Empty
22      22
23      52
24      Empty
25      83
26      26
27      Empty
28      57
```

## Match and collision analysis

The actual output matches the hand-predicted value at every index from 0
through 28. All 20 dataset keys were inserted. The four collisions are exactly
the occupied initial slots encountered when inserting `9`, `0`, `39`, and `4`.
The duplicate test and negative-key test are rejected before probing and do not
change the occupied-slot or collision counts.

| Measure | Expected | Actual | Match |
|:---|---:|---:|:---:|
| Input values | 20 | 20 | Yes |
| Successfully inserted | 20 | 20 | Yes |
| Collisions | 4 | 4 | Yes |
| Occupied positions | 20 | 20 | Yes |
| Empty positions | 9 | 9 | Yes |
| Load factor | 0.6897 | 0.6897 | Yes |

There were no mismatches to explain.

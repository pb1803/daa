# Strassen's Matrix Multiplication

## Theory
* **Goal:** Multiply two `n x n` matrices `A` and `B` faster than the standard `O(n^3)` algorithm.
* **Standard D&C:** Dividing each `n x n` matrix into four `(n/2) x (n/2)` blocks requires **8 recursive multiplications** and 4 additions -> `T(n) = 8T(n/2) + O(n^2) = O(n^3)`.
* **Strassen's Optimization:** Uses clever algebraic combinations to compute the product using only **7 recursive multiplications** (`P1` to `P7`) and 18 additions/subtractions.

## Algorithm (7 Products)
Divide `A` into blocks `A11, A12, A21, A22` and `B` into `B11, B12, B21, B22`:
```text
P1 = A11 * (B12 - B22)
P2 = (A11 + A12) * B22
P3 = (A21 + A22) * B11
P4 = A22 * (B21 - B11)
P5 = (A11 + A22) * (B11 + B22)
P6 = (A12 - A22) * (B21 + B22)
P7 = (A11 - A21) * (B11 + B12)

C11 = P5 + P4 - P2 + P6
C12 = P1 + P2
C21 = P3 + P4
C22 = P1 + P5 - P3 - P7
```

## Complexity
* **Recurrence:** `T(n) = 7T(n/2) + O(n^2)`
* **Time Complexity:** `O(n^(log_2(7)))` approx `O(n^2.81)`
* **Space Complexity:** `O(n^2)` for submatrix storage.

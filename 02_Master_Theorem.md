# Master Theorem & Recurrence Relations

## Theory
* **Purpose:** Provides a direct formula to solve divide-and-conquer recurrences of the form:
  `T(n) = a * T(n / b) + f(n)`
  where `a >= 1` (number of subproblems), `b > 1` (factor by which size shrinks), and `f(n)` is the cost of dividing and combining.
* **Critical Exponent:** Compare `f(n)` against `n^(log_b(a))`.

## Three Cases
1. **Case 1 (Leaves Dominate):** If `f(n) = O(n^(log_b(a) - e))` for some constant `e > 0`, then:
   `T(n) = Theta(n^(log_b(a)))`
2. **Case 2 (Balanced Work at Every Level):** If `f(n) = Theta(n^(log_b(a)))`, then:
   `T(n) = Theta(n^(log_b(a)) * log n)`
3. **Case 3 (Root Dominates):** If `f(n) = Omega(n^(log_b(a) + e))` for some `e > 0`, AND `a * f(n/b) <= k * f(n)` for some `k < 1` (regularity condition), then:
   `T(n) = Theta(f(n))`

## Quick Examples
* **Binary Search:** `T(n) = T(n/2) + 1` -> `a=1, b=2, n^0 = 1` -> Case 2 -> `Theta(log n)`
* **Merge Sort:** `T(n) = 2T(n/2) + n` -> `a=2, b=2, n^1 = n` -> Case 2 -> `Theta(n log n)`
* **Strassen's Matrix:** `T(n) = 7T(n/2) + n^2` -> `n^(log_2(7)) = n^2.81` -> Case 1 -> `Theta(n^2.81)`

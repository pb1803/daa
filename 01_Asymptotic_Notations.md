# Asymptotic Notations (Big-O, Omega, Theta)

## Theory
* **Purpose:** Asymptotic notations describe the running time or space growth of an algorithm as the input size `n` approaches infinity, independent of hardware or compiler.
* **Big-O (`O`) — Upper Bound (Worst Case):**
  * `f(n) = O(g(n))` if there exist positive constants `c` and `n0` such that `0 <= f(n) <= c * g(n)` for all `n >= n0`.
  * Represents the maximum time an algorithm can take.
* **Big-Omega (`Omega`) — Lower Bound (Best Case):**
  * `f(n) = Omega(g(n))` if there exist positive constants `c` and `n0` such that `0 <= c * g(n) <= f(n)` for all `n >= n0`.
  * Represents the minimum time an algorithm requires.
* **Big-Theta (`Theta`) — Tight Bound (Average / Exact Growth):**
  * `f(n) = Theta(g(n))` if there exist positive constants `c1, c2` and `n0` such that `0 <= c1 * g(n) <= f(n) <= c2 * g(n)` for all `n >= n0`.
  * Used when upper and lower bounds grow at the same rate.

## Example Comparison
* For `f(n) = 3n^2 + 5n + 2`:
  * `f(n) = O(n^2)` (with `c = 4, n0 = 6`)
  * `f(n) = Omega(n^2)` (with `c = 3, n0 = 1`)
  * `f(n) = Theta(n^2)`
* **Growth Hierarchy:** `O(1) < O(log n) < O(n) < O(n log n) < O(n^2) < O(2^n) < O(n!)`

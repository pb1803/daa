# Binomial Coefficient C(n, k): Recursion vs DP

## Theory
* **Definition:** `C(n, k)` counts the number of ways to choose `k` items from `n` distinct items.
* **Pascal's Identity (Recurrence):** Any specific item `n` is either **included** (choose `k-1` from remaining `n-1`) or **excluded** (choose `k` from remaining `n-1`):
  * `C(n, k) = C(n - 1, k - 1) + C(n - 1, k)`
  * **Base Cases:** `C(n, 0) = 1` and `C(n, n) = 1`
* **Why DP is Needed:** Pure recursion recomputes the same subproblems (like `C(n-2, k-1)`) exponentially many times. Storing values in a 2D table reduces time from exponential to polynomial.

## Algorithms
### 1. Pure Recursive Algorithm
```text
BinomialRec(n, k):
  if k == 0 or k == n:
    return 1
  return BinomialRec(n - 1, k - 1) + BinomialRec(n - 1, k)
```

### 2. Dynamic Programming Algorithm
```text
BinomialDP(n, k):
  Create table C[0..n][0..k]
  for i = 0 to n:
    for j = 0 to min(i, k):
      if j == 0 or j == i:
        C[i][j] = 1
      else:
        C[i][j] = C[i - 1][j - 1] + C[i - 1][j]
  return C[n][k]
```

## Complexity Comparison
* **Pure Recursion:** Time = `O(2^n)` *(worst case when `k = n/2`)*, Auxiliary Space = `O(n)` *(recursion stack depth)*.
* **Dynamic Programming:** Time = `O(n * k)`, Space = `O(n * k)` *(can be optimized to `O(k)` using a 1D array)*.

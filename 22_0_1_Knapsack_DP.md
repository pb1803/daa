# 0/1 Knapsack Problem (Dynamic Programming)

## Theory
* **Problem:** Given `n` items with weights `wt[0..n-1]` and values `val[0..n-1]`, and a knapsack of capacity `W`, maximize total value. Each item must be either **taken completely (`1`) or left out (`0`)**—no fractions allowed.
* **Why Greedy Fails:** Picking by highest `val/wt` ratio can leave unused space that prevents taking a higher-value combination.
* **Recurrence:** For item `i` and remaining capacity `w`:
  * If `wt[i-1] > w`: cannot include item -> `dp[i][w] = dp[i-1][w]`
  * Else: `dp[i][w] = max( dp[i-1][w], val[i-1] + dp[i-1][w - wt[i-1]] )`

## Algorithm
```text
Knapsack01(W, wt, val, n):
  Create table dp[0..n][0..W] initialized to 0

  for i = 1 to n:
    for w = 1 to W:
      if wt[i-1] <= w:
        include = val[i-1] + dp[i-1][w - wt[i-1]]
        exclude = dp[i-1][w]
        dp[i][w] = max(include, exclude)
      else:
        dp[i][w] = dp[i-1][w]

  return dp[n][W]
```

## Complexity
* **Time Complexity:** `O(n * W)` *(pseudo-polynomial time)*
* **Space Complexity:** `O(n * W)` *(can be reduced to `O(W)` using a 1D array iterated right-to-left)*

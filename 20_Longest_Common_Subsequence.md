# Longest Common Subsequence (LCS)

## Theory
* **Goal:** Given two strings `X` (length `m`) and `Y` (length `n`), find the longest subsequence present in both strings in the **same relative order** (characters need not be contiguous).
* **Recurrence Logic:**
  * If `X[i-1] == Y[j-1]` (characters match): `dp[i][j] = 1 + dp[i-1][j-1]`
  * If `X[i-1] != Y[j-1]` (mismatch): `dp[i][j] = max(dp[i-1][j], dp[i][j-1])`

## Algorithm
```text
LCS(X, Y, m, n):
  Create table dp[0..m][0..n] initialized with 0
  for i = 1 to m:
    for j = 1 to n:
      if X[i-1] == Y[j-1]:
        dp[i][j] = 1 + dp[i-1][j-1]
      else:
        dp[i][j] = max(dp[i-1][j], dp[i][j-1])
  return dp[m][n]
```

## Example (`X = "ABCBDAB"`, `Y = "BDCABA"`)
* Final `dp[7][6] = 4`
* Backtracking from bottom-right gives LCS = `"BCBA"` (or `"BDAB"`).

## Complexity
* **Time Complexity:** `O(m * n)`
* **Space Complexity:** `O(m * n)`

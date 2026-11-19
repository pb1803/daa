# Optimal Binary Search Tree (OBST - DP)

## Theory
* **Goal:** Given `n` sorted keys `K[1..n]` and their search frequencies/probabilities `freq[1..n]`, construct a Binary Search Tree (BST) that minimizes the **expected total search cost**.
* **Cost Formula:** Searching a node at depth `d` (where root is at level 1) takes `d` comparisons.
  `Total Cost = sum( freq[i] * level(K[i]) )` for `i = 1 to n`.
* **DP Recurrence:** For subarray of keys `i..j`, try every key `r` (`i <= r <= j`) as the root:
  `cost[i][j] = min( cost[i][r-1] + cost[r+1][j] ) + sum(freq[i..j])`
  *(Adding `sum(freq[i..j])` accounts for every node in both subtrees moving 1 level deeper under root `r`.)*

## Algorithm
```text
OptimalBST(keys, freq, n):
  Create cost[1..n+1][0..n] initialized to 0
  for i = 1 to n:
    cost[i][i] = freq[i]

  for L = 2 to n:                  // L = number of keys in chain
    for i = 1 to n - L + 1:
      j = i + L - 1
      cost[i][j] = infinity
      freqSum = sum(freq[i..j])
      for r = i to j:              // Try key r as root
        leftCost = (r > i) ? cost[i][r-1] : 0
        rightCost = (r < j) ? cost[r+1][j] : 0
        total = leftCost + rightCost + freqSum
        if total < cost[i][j]:
          cost[i][j] = total
  return cost[1][n]
```

## Complexity
* **Time Complexity:** `O(n^3)` *(can be optimized to `O(n^2)` using Knuth's optimization)*
* **Space Complexity:** `O(n^2)`

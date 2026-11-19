# Travelling Salesman Problem (TSP - Dynamic Programming)

## Theory
* **Problem:** Given `n` cities and a distance matrix `dist[i][j]`, find the shortest possible tour that visits every city **exactly once** and returns to the starting city `0`.
* **Why Naive Fails:** Checking all `(n - 1)!` permutations takes `O(n!)` time.
* **DP with Bitmasking (Held-Karp Algorithm):** Represent the subset of visited cities as an integer bitmask `mask` of `n` bits, and track the current city `pos`.
* **Recurrence:** `dp[mask][pos] = min( dist[pos][next] + dp[mask | (1 << next)][next] )` for all unvisited cities `next`.

## Algorithm
```text
TSP(mask, pos, n, dist, dp):
  if mask == (1 << n) - 1:             // All cities visited
    return dist[pos][0]                // Return to start city 0

  if dp[mask][pos] != -1:
    return dp[mask][pos]

  ans = infinity
  for city = 0 to n - 1:
    if (mask & (1 << city)) == 0:      // If city is not visited yet
      newAns = dist[pos][city] + TSP(mask | (1 << city), city, n, dist, dp)
      ans = min(ans, newAns)

  dp[mask][pos] = ans
  return ans
```

## Complexity
* **Time Complexity:** `O(n^2 * 2^n)` *(there are `2^n * n` states, each taking `O(n)` transitions—drastically faster than `O(n!)`)*
* **Space Complexity:** `O(n * 2^n)` for the memoization table.

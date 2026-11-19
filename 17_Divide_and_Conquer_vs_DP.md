# Generalized Divide & Conquer vs Dynamic Programming

## Theory
* **Divide & Conquer (D&C):** Breaks a problem into smaller **independent** (disjoint) subproblems, solves each recursively, and combines their answers. Because subproblems do not overlap, results are not stored.
* **Dynamic Programming (DP):** Solves problems having **Overlapping Subproblems** and **Optimal Substructure**. Instead of recomputing the same subproblem repeatedly, DP solves each subproblem once and stores its result in a table (Memoization or Tabulation).

## Generalized D&C Control Abstraction
```text
DivideAndConquer(P):
  if IsSmall(P):
    return SolveDirectly(P)
  Divide P into independent subproblems P1, P2, ..., Pk
  for i = 1 to k:
    yi = DivideAndConquer(Pi)
  return Combine(y1, y2, ..., yk)
```

## Key Differences
| Feature | Divide & Conquer | Dynamic Programming |
| :--- | :--- | :--- |
| **Subproblems** | Independent (disjoint) | Overlapping (shared repeatedly) |
| **Memory/Storage** | No table; uses recursion stack only | Uses DP table/array to cache results |
| **Approach** | Top-down recursion | Bottom-up (tabulation) or Top-down (memoization) |
| **Examples** | Merge Sort, Quick Sort, Binary Search | 0/1 Knapsack, LCS, Floyd-Warshall, MCM |

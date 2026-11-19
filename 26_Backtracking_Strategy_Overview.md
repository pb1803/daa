# Backtracking: General Strategy & Control Abstraction

## Theory
* **Definition:** Backtracking is a systematic, depth-first search (DFS) method for solving constraint satisfaction and combinatorial problems by building solutions **one component at a time**.
* **Bounding Function & Pruning:** Whenever a partial solution violates a constraint (detected via a **bounding function**), we immediately abandon ("prune") that branch and **backtrack** to the previous decision point—avoiding brute-force exploration of invalid subtrees.
* **State Space Tree:** A conceptual tree where root = initial state, edges = choices, and leaves = complete solutions.

## General Recursive Control Abstraction
```text
Backtrack(k):
  // k is the index of the current decision variable x[k]
  for each possible value v in Domain(x[k]):
    x[k] = v
    if Bound(x[1..k]) is TRUE:          // Check constraints (promising node)
      if IsSolution(x[1..k]):
        Print(x[1..k])
      else:
        Backtrack(k + 1)               // Explore deeper
    // Otherwise prune branch and try next value
```

## Classic Applications
* **N-Queens Problem**, **Sum of Subsets**, **Graph Coloring**, **Hamiltonian Cycle**, and **Sudoku Solver**.

# Greedy Method: General Strategy & Properties

## Theory
* **Definition:** A greedy algorithm builds a solution step-by-step, always picking the choice that looks best **at that immediate moment** (locally optimal) without reconsidering past choices, hoping it leads to a globally optimal solution.
* **Two Key Ingredients Required:**
  1. **Greedy Choice Property:** A globally optimal solution can be reached by making a locally optimal (greedy) choice at each step.
  2. **Optimal Substructure:** An optimal solution to the overall problem contains optimal solutions to its subproblems.

## General Control Abstraction
```text
Greedy(A, n):
  Solution = empty_set
  for i = 1 to n:
    x = Select(A)                  // Pick best available candidate
    if Feasible(Solution, x):      // Check constraints
      Solution = Union(Solution, x)
  return Solution
```

## Greedy vs Dynamic Programming
* **Greedy:** Makes one irreversible choice per step (top-down); faster, works only when greedy choice property holds (e.g., Fractional Knapsack, Dijkstra, Kruskal).
* **Dynamic Programming:** Evaluates all choices and stores subproblem answers (bottom-up/memoized); works even when greedy fails (e.g., 0/1 Knapsack, Coin Change).

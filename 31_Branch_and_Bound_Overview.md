# Branch and Bound: Concept & Search Strategies

## Theory
* **Definition:** Branch and Bound (B&B) is an algorithm design technique used mainly for **optimization problems** (minimization or maximization). It builds a state-space tree, computes a **bound** (best possible objective value reachable from a node), and **kills (prunes)** any node whose bound is worse than the best solution found so far (`upper/cost`).
* **Backtracking vs Branch & Bound:**
  * **Backtracking:** Uses DFS, finds *all* or *any* feasible solution for constraint satisfaction problems.
  * **Branch & Bound:** Uses BFS/Least-Cost search with bounding functions to find the *optimal* solution for optimization problems.

## Three Exploration Strategies
1. **FIFO Branch & Bound (Breadth-First):** Uses a **Queue**; explores nodes level by level.
2. **LIFO Branch & Bound (Depth-First):** Uses a **Stack**; explores deepest nodes first.
3. **LC (Least-Cost) Branch & Bound:** Uses a **Min-Heap (Priority Queue)** ordered by a cost function `c_hat(x)` (estimated lower bound). Always expands the most promising node first, reaching the optimal solution fastest.

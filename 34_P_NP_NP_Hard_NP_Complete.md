# Complexity Classes: P, NP, NP-Hard, and NP-Complete

## Theory & Definitions
* **Class P (Polynomial Time):**
  * Set of decision problems that can be **solved** by a deterministic Turing machine in polynomial time `O(n^k)`.
  * *Examples:* Binary Search, Merge Sort, Dijkstra's Shortest Path, MST.
* **Class NP (Non-Deterministic Polynomial Time):**
  * Set of decision problems whose proposed solution ("certificate") can be **verified** in polynomial time `O(n^k)`.
  * Note: `P` is a subset of `NP` (`P <= NP`), because any problem solvable in polynomial time can also be verified in polynomial time.
* **NP-Hard:**
  * A problem `H` is **NP-Hard** if **every problem in NP can be reduced to `H` in polynomial time** (`L <=_p H`).
  * `H` is at least as hard as the hardest problems in NP. It does **not** have to belong to NP (e.g., Halting Problem).
* **NP-Complete (NPC):**
  * A problem `C` is **NP-Complete** if:
    1. `C` is in **NP** (verifiable in polynomial time), **AND**
    2. `C` is **NP-Hard** (every problem in NP reduces to `C` in polynomial time).
  * *Examples:* Boolean Satisfiability (SAT / 3-SAT), Travelling Salesman Decision Problem, Clique, Vertex Cover, Hamiltonian Cycle, 0/1 Knapsack Decision Problem.

## Relationship Summary
* If any single NP-Complete problem is ever solved in polynomial time, then **`P = NP`**.
* **Diagram Logic:** `P` lies inside `NP`; `NP-Complete` is the exact intersection `NP ∩ NP-Hard`.

# M-Coloring / Graph Coloring Problem (Backtracking)

## Theory
* **Problem:** Given an undirected graph `G` with `V` vertices and `m` colors, assign a color (`1` to `m`) to every vertex such that **no two adjacent vertices share the same color**.
* **Chromatic Number:** The minimum number of colors `m` required to properly color a graph.
* **Backtracking Strategy:** Assign colors to vertices `0` through `V - 1`. At vertex `v`, try colors `1` to `m`. Check `IsSafe(v, c)` to ensure none of `v`'s neighbors already have color `c`. If valid, recurse to `v + 1`; otherwise backtrack.

## Algorithm
```text
GraphColoring(Graph, m, V, color, v):
  if v == V:
    Print(color[0..V-1])
    return true

  for c = 1 to m:
    if IsSafe(Graph, V, color, v, c):
      color[v] = c                     // Assign color c
      if GraphColoring(Graph, m, V, color, v + 1):
        return true
      color[v] = 0                     // Backtrack
  return false

IsSafe(Graph, V, color, v, c):
  for u = 0 to V - 1:
    if Graph[v][u] == 1 and color[u] == c:
      return false
  return true
```

## Complexity
* **Time Complexity:** `O(m^V)` *(at most `m` color choices for each of the `V` vertices)*
* **Space Complexity:** `O(V)` for the `color[]` array and recursion stack.

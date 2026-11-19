# Hamiltonian Cycle (Backtracking)

## Theory
* **Definition:** A **Hamiltonian Cycle** in an undirected or directed graph is a closed path that visits **every vertex exactly once** and returns to the starting vertex.
* **Difference from Eulerian Cycle:** Eulerian visits every *edge* once; Hamiltonian visits every *vertex* once.
* **Backtracking Strategy:** Start at vertex `0` (`path[0] = 0`). At position `pos`, try adding a vertex `v` (`1` to `V - 1`) that:
  1. Has an edge from `path[pos - 1]`.
  2. Has not been visited yet in `path[0..pos-1]`.
  3. When `pos == V`, verify there is an edge from `path[V - 1]` back to `path[0]`.

## Algorithm
```text
HamCycle(Graph, path, pos, V):
  if pos == V:
    if Graph[path[pos - 1]][path[0]] == 1:
      Print(path)
      return true
    return false

  for v = 1 to V - 1:
    if IsValidVertex(v, Graph, path, pos):
      path[pos] = v
      if HamCycle(Graph, path, pos + 1, V):
        return true
      path[pos] = -1                   // Backtrack
  return false

IsValidVertex(v, Graph, path, pos):
  if Graph[path[pos - 1]][v] == 0: return false
  for i = 0 to pos - 1:
    if path[i] == v: return false
  return true
```

## Complexity
* **Time Complexity:** `O(V!)` *(worst-case permutation search)*
* **Space Complexity:** `O(V)` for `path[]` and recursion depth.

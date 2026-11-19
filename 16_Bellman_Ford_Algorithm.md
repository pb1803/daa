# Bellman-Ford Algorithm (Single-Source Shortest Path)

## Theory
* **Goal:** Find shortest paths from a single `source` to all vertices in a weighted directed graph, **even when negative edge weights exist**. Also detects **negative weight cycles**.
* **Working Principle:** Any simple shortest path in a graph of `V` vertices has at most `V - 1` edges. Therefore, we **relax every edge in the graph `V - 1` times**.
* **Negative Cycle Check:** Perform one extra (`V`-th) pass over all edges. If any distance still decreases, a negative weight cycle exists reachable from the source.

## Algorithm
```text
BellmanFord(V, Edges, source):
  dist[0..V-1] = infinity
  dist[source] = 0

  for i = 1 to V - 1:
    for each edge (u, v, w) in Edges:
      if dist[u] != infinity and dist[u] + w < dist[v]:
        dist[v] = dist[u] + w

  // Check for negative weight cycle
  for each edge (u, v, w) in Edges:
    if dist[u] != infinity and dist[u] + w < dist[v]:
      return "Negative Weight Cycle Exists"

  return dist[]
```

## Complexity
* **Time Complexity:** `O(V * E)` *(slower than Dijkstra, but handles negative weights)*
* **Space Complexity:** `O(V)` for distance array.

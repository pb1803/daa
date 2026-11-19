# Dijkstra's Single-Source Shortest Path Algorithm

## Theory
* **Goal:** Find the shortest path distance from a single `source` vertex to all other vertices in a weighted graph with **non-negative edge weights (`w >= 0`)**.
* **Greedy Strategy:** Maintain a distance array `dist[]` initialized to `infinity` (`dist[source] = 0`). Repeatedly pick the unvisited vertex `u` with the **smallest known distance**, mark it finalized, and **relax** all its outgoing edges:
  `if dist[u] + weight(u, v) < dist[v]: dist[v] = dist[u] + weight(u, v)`
* **Limitation:** Fails if the graph contains **negative weight edges** (because finalized vertices are never re-evaluated).

## Algorithm
```text
Dijkstra(Graph, V, source):
  dist[0..V-1] = infinity
  dist[source] = 0
  Min-Heap PQ stores (0, source)

  while PQ is not empty:
    (d, u) = PQ.extractMin()
    if d > dist[u]: continue

    for each neighbor v of u with weight w:
      if dist[u] + w < dist[v]:
        dist[v] = dist[u] + w
        PQ.insert((dist[v], v))
  return dist[]
```

## Complexity
* **With Min-Heap & Adjacency List:** `O((V + E) log V)` = `O(E log V)`
* **With Adjacency Matrix:** `O(V^2)`
* **Space Complexity:** `O(V + E)`

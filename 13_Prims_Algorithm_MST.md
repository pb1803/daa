# Prim's Algorithm (Minimum Spanning Tree)

## Theory
* **Goal:** Find a Minimum Spanning Tree (MST) of a connected, undirected, weighted graph—a subset of `V - 1` edges connecting all `V` vertices with minimum total weight and no cycles.
* **Greedy Strategy:** Start from any arbitrary vertex and grow the MST one vertex at a time. At every step, pick the **minimum-weight edge** that connects a vertex **inside** the MST to a vertex **outside** the MST.
* **Best For:** Dense graphs (when implemented with an adjacency matrix or Priority Queue).

## Algorithm
```text
PrimsMST(Graph, V, start):
  Initialize key[0..V-1] = infinity, inMST[0..V-1] = false
  key[start] = 0
  Min-Heap PQ stores (0, start)

  while PQ is not empty:
    (w, u) = PQ.extractMin()
    if inMST[u]: continue
    inMST[u] = true
    mstWeight += w

    for each neighbor v of u with edge weight weight(u, v):
      if not inMST[v] and weight(u, v) < key[v]:
        key[v] = weight(u, v)
        PQ.insert((key[v], v))
  return mstWeight
```

## Complexity
* **With Binary Min-Heap & Adjacency List:** `O((V + E) log V)` = `O(E log V)`
* **With Adjacency Matrix (array scan):** `O(V^2)`
* **Space Complexity:** `O(V + E)`

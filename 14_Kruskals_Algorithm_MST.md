# Kruskal's Algorithm (Minimum Spanning Tree)

## Theory
* **Goal:** Build a Minimum Spanning Tree (MST) by selecting `V - 1` minimum-weight edges without forming any cycles.
* **Greedy Strategy:** Sort **all edges** in ascending order of weight. Pick the smallest edge; if adding it does **not** form a cycle (checked via **Disjoint Set Union / Union-Find**), include it in the MST. Repeat until `V - 1` edges are chosen.
* **Best For:** Sparse graphs (`E` is much smaller than `V^2`).

## Algorithm
```text
KruskalsMST(V, Edges):
  Sort Edges in ascending order of weight
  Initialize Disjoint Set (parent[i] = i for i = 0 to V-1)
  mstWeight = 0, edgeCount = 0

  for each edge (u, v, w) in Edges:
    if Find(u) != Find(v):             // No cycle formed
      Union(u, v)
      mstWeight += w
      edgeCount += 1
      if edgeCount == V - 1:
        break
  return mstWeight
```

## Complexity
* **Time Complexity:** `O(E log E)` *(sorting edges takes `O(E log E)`, Union-Find takes `O(E * alpha(V))` approx `O(E)`)*
* **Space Complexity:** `O(V + E)`

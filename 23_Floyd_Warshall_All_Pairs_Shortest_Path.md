# Floyd-Warshall Algorithm (All-Pairs Shortest Path)

## Theory
* **Goal:** Find shortest path distances between **every pair of vertices `(i, j)`** in a weighted directed graph (handles positive and negative edge weights, provided there are no negative cycles).
* **DP Strategy:** Consider intermediate vertices `k` from `0` to `V - 1` one by one. For every pair `(i, j)`, check if going through vertex `k` (`i -> k -> j`) gives a shorter path than the direct path `i -> j`.
* **Recurrence:** `dist[i][j] = min( dist[i][j], dist[i][k] + dist[k][j] )`

## Algorithm
```text
FloydWarshall(Graph, V):
  Create dist[0..V-1][0..V-1]
  Initialize dist[i][j] = weight(i, j) (0 if i == j, infinity if no edge)

  for k = 0 to V - 1:              // Intermediate vertex
    for i = 0 to V - 1:            // Source vertex
      for j = 0 to V - 1:          // Destination vertex
        if dist[i][k] != infinity and dist[k][j] != infinity:
          if dist[i][k] + dist[k][j] < dist[i][j]:
            dist[i][j] = dist[i][k] + dist[k][j]

  return dist[][]
```

## Complexity
* **Time Complexity:** `O(V^3)` *(three nested loops over `V`)*
* **Space Complexity:** `O(V^2)` *(for the distance matrix)*

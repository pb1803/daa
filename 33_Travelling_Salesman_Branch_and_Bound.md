# Travelling Salesman Problem (LC Branch & Bound)

## Theory
* **Goal:** Find the minimum-cost tour visiting all `n` cities once and returning to start city `0` using **Least-Cost Branch and Bound** with **Row and Column Matrix Reduction**.
* **Matrix Reduction (Lower Bound):** Every tour must leave each row once and enter each column once. Subtracting the minimum value of each row and then each column creates at least one `0` in every row and column. The **sum of all subtracted values** gives the initial lower bound `cost(root)`.
* **Child Node Cost Formula:** Moving from city `u` to city `v`:
  1. Start with parent's reduced matrix `M`.
  2. Set all entries in **row `u`** and **column `v`** to `infinity`, and set `M[v][0] = infinity` (prevent premature return to start).
  3. Reduce `M` again to get `reductionCost`.
  4. `cost(v) = cost(u) + M_parent[u][v] + reductionCost`.

## Algorithm
```text
TSP_LCBB(dist, n):
  (reducedMat, initCost) = ReduceMatrix(dist)
  PQ = Min-Heap ordered by node.cost
  PQ.insert(Node(city=0, level=0, cost=initCost, matrix=reducedMat, path=[0]))
  minTourCost = infinity

  while PQ is not empty:
    curr = PQ.extractMin()
    if curr.cost >= minTourCost: continue

    if curr.level == n - 1:
      minTourCost = min(minTourCost, curr.cost)
      continue

    for nextCity = 0 to n - 1:
      if nextCity not in curr.path and curr.matrix[curr.city][nextCity] != infinity:
        childMat = Copy(curr.matrix)
        Set row curr.city, col nextCity, and childMat[nextCity][0] to infinity
        (childMat, rCost) = ReduceMatrix(childMat)
        totalCost = curr.cost + curr.matrix[curr.city][nextCity] + rCost
        if totalCost < minTourCost:
          PQ.insert(Node(nextCity, curr.level + 1, totalCost, childMat, curr.path + [nextCity]))

  return minTourCost
```

## Complexity
* **Worst-Case Time:** `O(n^2 * 2^n)` to `O(n!)` *(pruning eliminates most branches in practice)*
* **Space Complexity:** `O(n^2 * number_of_live_nodes)`

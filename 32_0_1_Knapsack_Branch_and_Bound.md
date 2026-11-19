# 0/1 Knapsack using LC Branch and Bound

## Theory
* **Setup:** Convert maximization of profit into **minimization** by negating profits (`-p[i]`). Sort items in **descending order of profit/weight ratio (`p[i] / w[i]`)**.
* **Two Bounds at Each Node:**
  * **`cost` (Current Actual Cost):** Negative sum of profits of items already included (`-currentProfit`).
  * **`upper` (Upper Bound / Lower Bound on Profit):** Estimated best possible profit from this node computed **greedily using fractional knapsack** on remaining capacity.
* **Pruning Rule:** Maintain a global minimum `bestUpper`. If a node's `upper > bestUpper` (or weight exceeds `W`), kill/prune the node immediately.

## Algorithm
```text
KnapsackLCBB(W, items, n):
  Sort items in descending order of p[i] / w[i]
  Create Priority Queue PQ (ordered by lowest upper bound)
  root = Node(level=0, profit=0, weight=0)
  root.upper = ComputeFractionalBound(root, W, items, n)
  bestUpper = root.upper
  PQ.insert(root)

  while PQ is not empty:
    u = PQ.extractMin()
    if u.upper > bestUpper or u.level == n:
      continue

    // Left Child: Include next item (u.level + 1)
    if u.weight + items[u.level].w <= W:
      left = Node(u.level + 1, u.profit - items[u.level].p, u.weight + items[u.level].w)
      left.upper = ComputeFractionalBound(left, W, items, n)
      bestUpper = min(bestUpper, left.profit)
      if left.upper <= bestUpper: PQ.insert(left)

    // Right Child: Exclude next item
    right = Node(u.level + 1, u.profit, u.weight)
    right.upper = ComputeFractionalBound(right, W, items, n)
    if right.upper <= bestUpper: PQ.insert(right)

  return -bestUpper
```

## Complexity
* **Worst-Case Time:** `O(2^n)` *(in practice much faster due to tight fractional bound pruning)*
* **Space Complexity:** `O(2^n)` for active nodes in the Priority Queue.

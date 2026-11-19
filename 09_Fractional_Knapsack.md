# Fractional Knapsack Problem (Greedy)

## Theory
* **Problem:** Given `n` items with weights `w[i]` and profits `p[i]`, and a knapsack of capacity `W`, maximize total profit. Unlike 0/1 Knapsack, **items can be broken into fractions**.
* **Greedy Strategy:** Always pick the item with the highest **profit-to-weight ratio (`p[i] / w[i]`)** first. Take as much of it as fits; if the remaining capacity is smaller than the next item's weight, take the fraction `remaining_W / w[i]`.

## Algorithm
```text
FractionalKnapsack(W, items, n):
  For each item i, compute ratio[i] = p[i] / w[i]
  Sort items in descending order of ratio[i]
  totalProfit = 0.0

  for i = 1 to n:
    if W == 0:
      break
    if w[i] <= W:
      totalProfit += p[i]
      W -= w[i]
    else:
      totalProfit += p[i] * (W / w[i])
      W = 0
  return totalProfit
```

## Complexity
* **Time Complexity:** `O(n log n)` *(dominated by sorting items by ratio)*
* **Space Complexity:** `O(1)` *(excluding input storage)*

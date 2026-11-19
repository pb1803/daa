# Optimal Merge Pattern (Greedy)

## Theory
* **Problem:** Given `n` sorted files of sizes `s1, s2, ..., sn`, merge them pairwise into a single sorted file with **minimum total record movements**. Merging two files of sizes `a` and `b` costs `a + b` operations.
* **Greedy Strategy:** Always merge the **two smallest files** first using a Min-Heap. Larger files are merged as late as possible so their elements are copied fewer times.
* **Weighted External Path Length:** Total cost equals `sum(file_size[i] * depth[i])` in the merge tree.

## Algorithm
```text
OptimalMerge(files, n):
  Insert all n file sizes into a Min-Heap H
  totalCost = 0

  while H.size() > 1:
    first = H.extractMin()
    second = H.extractMin()
    mergeCost = first + second
    totalCost += mergeCost
    H.insert(mergeCost)

  return totalCost
```

## Complexity
* **Time Complexity:** `O(n log n)` *(building heap `O(n)` + `n-1` heap operations of `O(log n)`)*
* **Space Complexity:** `O(n)` for the Min-Heap.

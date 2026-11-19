# Binary Search (Divide & Conquer)

## Theory
* **Goal:** Find the position of a `target` element inside a **sorted** array of size `n`.
* **Working Principle:** Compare `target` with the middle element `arr[mid]`. If equal, return `mid`. If smaller, discard the right half; if larger, discard the left half. Each step cuts the search space in half.
* **Prerequisite:** The input array must be sorted in ascending or descending order.

## Algorithm
```text
BinarySearch(arr, low, high, target):
  while low <= high:
    mid = low + (high - low) / 2
    if arr[mid] == target:
      return mid
    else if arr[mid] < target:
      low = mid + 1
    else:
      high = mid - 1
  return -1
```

## Complexity & Recurrence
* **Recurrence:** `T(n) = T(n / 2) + O(1)`
* **Best Case:** `O(1)` *(target found at first middle check)*
* **Average / Worst Case:** `O(log n)`
* **Space Complexity:** `O(1)` iterative, `O(log n)` recursive stack

# Quick Sort

## Theory
* **Paradigm:** Divide and Conquer (in-place sorting).
* **Working Principle:**
  1. **Pivot Selection:** Pick an element as the `pivot` (first, last, middle, or random).
  2. **Partitioning:** Rearrange the array so all elements `<= pivot` move to its left and all elements `> pivot` move to its right. The pivot lands in its final sorted position.
  3. **Recursion:** Recursively sort the left and right subarrays around the pivot.
* **Properties:** In-place (`O(log n)` stack space), unstable sort, faster in practice than Merge Sort due to cache locality.

## Algorithm
```text
QuickSort(arr, low, high):
  if low < high:
    p = Partition(arr, low, high)
    QuickSort(arr, low, p - 1)
    QuickSort(arr, p + 1, high)

Partition(arr, low, high):
  pivot = arr[high]
  i = low - 1
  for j = low to high - 1:
    if arr[j] <= pivot:
      i = i + 1
      swap(arr[i], arr[j])
  swap(arr[i + 1], arr[high])
  return i + 1
```

## Complexity
* **Best / Average Case:** `T(n) = 2T(n/2) + O(n)` -> `O(n log n)` *(balanced splits)*
* **Worst Case:** `T(n) = T(n-1) + O(n)` -> `O(n^2)` *(already sorted array when picking first/last pivot)*
* **Space Complexity:** `O(log n)` average recursion stack, `O(n)` worst-case stack.

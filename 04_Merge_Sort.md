# Merge Sort

## Theory
* **Paradigm:** Divide and Conquer.
* **Working Principle:**
  1. **Divide:** Split the array into two equal halves at `mid = (low + high) / 2`.
  2. **Conquer:** Recursively sort both left and right subarrays until single elements remain.
  3. **Combine:** Merge the two sorted halves into a single sorted array using two pointers.
* **Properties:** Stable sort (preserves relative order of equal elements), not in-place (requires auxiliary array).

## Algorithm
```text
MergeSort(arr, low, high):
  if low < high:
    mid = (low + high) / 2
    MergeSort(arr, low, mid)
    MergeSort(arr, mid + 1, high)
    Merge(arr, low, mid, high)

Merge(arr, low, mid, high):
  Copy arr[low..mid] into L[] and arr[mid+1..high] into R[]
  i = 0, j = 0, k = low
  while i < len(L) and j < len(R):
    if L[i] <= R[j]:
      arr[k++] = L[i++]
    else:
      arr[k++] = R[j++]
  Copy remaining elements of L[] and R[] into arr[]
```

## Complexity
* **Recurrence:** `T(n) = 2T(n/2) + O(n)`
* **Time Complexity:** `O(n log n)` in Best, Average, and Worst cases.
* **Space Complexity:** `O(n)` auxiliary space for merging.

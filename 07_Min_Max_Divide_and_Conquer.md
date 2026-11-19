# Finding Minimum and Maximum (Divide & Conquer)

## Theory
* **Goal:** Find both the minimum and maximum elements in an array of `n` elements using the fewest possible comparisons.
* **Naive Approach:** Scan linearly comparing every element against current `min` and `max` -> takes `2(n - 1)` comparisons.
* **Divide & Conquer Approach:** Split the array into two halves, recursively find `(min1, max1)` for the left half and `(min2, max2)` for the right half, then return `(min(min1, min2), max(max1, max2))`.

## Algorithm
```text
FindMinMax(arr, low, high):
  if low == high:                          // 1 element
    return (arr[low], arr[low])
  if high == low + 1:                      // 2 elements (1 comparison)
    if arr[low] < arr[high]:
      return (arr[low], arr[high])
    else:
      return (arr[high], arr[low])

  mid = (low + high) / 2
  (min1, max1) = FindMinMax(arr, low, mid)
  (min2, max2) = FindMinMax(arr, mid + 1, high)
  return (min(min1, min2), max(max1, max2))
```

## Complexity
* **Recurrence:** `T(n) = 2T(n/2) + 2` with `T(2) = 1`, `T(1) = 0`
* **Total Comparisons:** `T(n) = (3n / 2) - 2` (25% fewer comparisons than naive approach).
* **Time Complexity:** `O(n)`
* **Space Complexity:** `O(log n)` recursion stack.

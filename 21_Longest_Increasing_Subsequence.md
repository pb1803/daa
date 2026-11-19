# Longest Increasing Subsequence (LIS)

## Theory
* **Goal:** Given an unsorted array `arr` of size `n`, find the length of the longest subsequence whose elements are in **strictly increasing order** (`arr[i1] < arr[i2] < ... < arr[ik]`).
* **DP State:** Let `lis[i]` represent the length of the longest increasing subsequence **ending at index `i`**. Initially, every element forms a subsequence of length `1`.
* **Transition:** For each `i` from `1` to `n-1`, check all previous indices `j < i`. If `arr[j] < arr[i]`, we can extend the subsequence ending at `j`: `lis[i] = max(lis[i], lis[j] + 1)`.

## Algorithm
```text
LIS(arr, n):
  Create array lis[0..n-1] initialized to 1
  maxLen = 1

  for i = 1 to n - 1:
    for j = 0 to i - 1:
      if arr[j] < arr[i] and lis[j] + 1 > lis[i]:
        lis[i] = lis[j] + 1
    if lis[i] > maxLen:
      maxLen = lis[i]

  return maxLen
```

## Example
* For `arr = [10, 22, 9, 33, 21, 50, 41, 60]`:
  `lis = [1, 2, 1, 3, 2, 4, 4, 5]` -> **LIS Length = 5** (`[10, 22, 33, 50, 60]`).

## Complexity
* **Time Complexity:** `O(n^2)` *(DP approach; can be improved to `O(n log n)` using Patience Sorting / Binary Search)*
* **Space Complexity:** `O(n)`

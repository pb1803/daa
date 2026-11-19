# Sum of Subsets Problem (Backtracking)

## Theory
* **Problem:** Given a set of `n` positive integers sorted in ascending order `w[0..n-1]` and a target sum `M`, find all subsets whose elements sum exactly to `M`.
* **Bounding Functions (Pruning):** Let `currSum` be the sum included so far, and `remSum` be the sum of remaining unconsidered elements. We prune a branch immediately if:
  1. `currSum + w[k] > M` *(since array is sorted, adding `w[k]` or any later element exceeds `M`)*
  2. `currSum + remSum < M` *(even taking all remaining elements cannot reach `M`)*

## Algorithm
```text
SumOfSubsets(currSum, k, remSum, w, x, M):
  // Include w[k]
  x[k] = 1
  if currSum + w[k] == M:
    PrintSubset(x, w)
  else if currSum + w[k] + w[k+1] <= M:
    SumOfSubsets(currSum + w[k], k + 1, remSum - w[k], w, x, M)

  // Exclude w[k] (Backtrack)
  x[k] = 0
  if (currSum + remSum - w[k] >= M) and (currSum + w[k+1] <= M):
    SumOfSubsets(currSum, k + 1, remSum - w[k], w, x, M)
```

## Complexity
* **Time Complexity:** `O(2^n)` in the worst case *(binary decision tree of include/exclude)*
* **Space Complexity:** `O(n)` for recursion stack and solution vector `x[]`.

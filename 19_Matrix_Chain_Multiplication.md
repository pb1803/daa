# Matrix Chain Multiplication (DP)

## Theory
* **Goal:** Given `n` matrices `A1, A2, ..., An`, find the optimal way to parenthesize them so the total number of scalar multiplications is minimized.
* **Key Principle:** Matrix multiplication is associative (`(AB)C = A(BC)`), so the final product matrix never changes, but the operation count changes drastically.
* **Cost Rule:** Matrix `i` has dimensions `p[i-1] x p[i]`. Multiplying an `(a x b)` matrix by a `(b x c)` matrix costs `a * b * c` multiplications.
* **Recurrence:**
  * `m[i][j] = 0` if `i == j`
  * `m[i][j] = min( m[i][k] + m[k+1][j] + p[i-1] * p[k] * p[j] )` for all split points `k` from `i` to `j - 1`.

## Algorithm
```text
MatrixChainOrder(p, n):
  Create tables m[1..n][1..n] and s[1..n][1..n]
  for i = 1 to n:
    m[i][i] = 0

  for L = 2 to n:                  // L = chain length
    for i = 1 to n - L + 1:
      j = i + L - 1
      m[i][j] = infinity
      for k = i to j - 1:          // Test every split point k
        cost = m[i][k] + m[k+1][j] + p[i-1] * p[k] * p[j]
        if cost < m[i][j]:
          m[i][j] = cost
          s[i][j] = k              // Store optimal split index
  return m[1][n]
```

## Worked Example (`A: 10x20, B: 20x30, C: 30x40, D: 40x10`)
* Dimensions array: `p = [10, 20, 30, 40, 10]`
* Length 2: `m[1][2] = 6000`, `m[2][3] = 24000`, `m[3][4] = 12000`
* Length 3: `m[1][3] = 18000` (`k=2`), `m[2][4] = 18000` (`k=2`)
* Length 4: `m[1][4] = 20000` (`k=1`) -> Optimal Parenthesization: `(A(B(CD)))`

## Complexity
* **Time Complexity:** `O(n^3)` *(three nested loops: `L`, `i`, `k`)*
* **Space Complexity:** `O(n^2)` *(for tables `m` and `s`)*

# N-Queens Problem (Backtracking)

## Theory
* **Problem:** Place `N` queens on an `N x N` chessboard such that **no two queens attack each other**—meaning no two queens share the same **row, column, or diagonal**.
* **Backtracking Strategy:** Place one queen per row (from row `0` to `N - 1`). For each column `col` in the current row, check if `(row, col)` is safe using `IsSafe()`. If safe, place the queen and recurse to `row + 1`. If no column works, backtrack and move the previous queen.
* **Diagonal Check:** Two cells `(r1, c1)` and `(r2, c2)` share a diagonal if `abs(r1 - r2) == abs(c1 - c2)`.

## Algorithm
```text
SolveNQueens(board, row, N):
  if row == N:
    Print(board)
    return true

  for col = 0 to N - 1:
    if IsSafe(board, row, col, N):
      board[row][col] = 1              // Place queen
      SolveNQueens(board, row + 1, N)
      board[row][col] = 0              // Backtrack (remove queen)

IsSafe(board, row, col, N):
  // Check column above
  for i = 0 to row - 1:
    if board[i][col] == 1: return false
  // Check upper-left diagonal
  for i = row - 1, j = col - 1; i >= 0 and j >= 0; i--, j--:
    if board[i][j] == 1: return false
  // Check upper-right diagonal
  for i = row - 1, j = col + 1; i >= 0 and j < N; i--, j++:
    if board[i][j] == 1: return false
  return true
```

## Complexity
* **Time Complexity:** `O(N!)` *(worst-case state space; pruning reduces practical runtime significantly)*
* **Space Complexity:** `O(N^2)` for board (or `O(N)` using a 1D array `pos[row] = col`).

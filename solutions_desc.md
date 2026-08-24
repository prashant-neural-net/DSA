# DSA Practice & Build Activity Log


## [2026-08-24 17:45:24 UTC] feat(dsa/backtracking): add N-Queens constraint satisfaction solver

**Module:** `dsa/backtracking`  
**Status:** Verified & Compiled  

### Summary
Implemented backtracking solution with bitmasking optimization for diagonal collision detection.

```cpp
void solveNQueens(int row, int n, int& count, int cols, int diag1, int diag2) {
    if (row == n) { count++; return; }
    int availablePositions = ((1 << n) - 1) & ~(cols | diag1 | diag2);
    while (availablePositions) {
        int p = availablePositions & -availablePositions;
        availablePositions -= p;
        solveNQueens(row + 1, n, count, cols | p, (diag1 | p) << 1, (diag2 | p) >> 1);
    }
}
```

# Memoization

### Leetcode 329. Longest Increasing Path in a Matrix

Given an m x n integers matrix, return the length of the longest increasing path in matrix.

From each cell, you can either move in four directions: left, right, up, or down. You may not move diagonally or move outside the boundary (i.e., wrap-around is not allowed).

#### Example :
```
Input: matrix = [[9,9,4],[6,6,8],[2,1,1]]
Output: 4
Explanation: The longest increasing path is [1, 2, 6, 9].
```

#### Solution :
```
class Solution {
    int[][] dirs = {{0,1}, {0,-1}, {1,0}, {-1,0}};
    public int longestIncreasingPath(int[][] matrix) {
        int m = matrix.length, n = matrix[0].length;
        int[][] cache = new int[m][n];
        int res = 0;
        for(int i = 0; i < m; i++) {
            for(int j = 0; j < n; j++) {
                res = Math.max(res, dfs(matrix, i, j, cache));
            }
        }
        return res;
    }
    
    public int dfs(int[][] matrix, int i, int j, int[][] cache) {
        int m = matrix.length, n = matrix[0].length;
        if(cache[i][j] != 0) return cache[i][j];
        int res = 0;
        for(int[] dir : dirs) {
            int x = dir[0] + i;
            int y = dir[1] + j;
            if(x < 0 || x >= m || y < 0 || y >= n || matrix[x][y] <= matrix[i][j]) continue;
            res = Math.max(res, dfs(matrix, x, y, cache));
        }
        res += 1;
        cache[i][j] = res;
        return res;
    }
}
```

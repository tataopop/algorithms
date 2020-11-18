# DFS

### Leetcode 695 : Max Area of Island

Given a non-empty 2D array grid of 0's and 1's, an island is a group of 1's (representing land) connected 4-directionally (horizontal or vertical.) You may assume all four edges of the grid are surrounded by water.

Find the maximum area of an island in the given 2D array. (If there is no island, the maximum area is 0.)

#### Solution :
```
class Solution {
    int[][] dirs = new int[][]{{1,0},{-1,0},{0,1},{0,-1}};
    public int maxAreaOfIsland(int[][] grid) {
        int res = 0;
        for(int i = 0; i < grid.length; i++) {
            for(int j = 0; j < grid[0].length; j++) {
                if(grid[i][j] == 0) continue;
                res = Math.max(res, dfs(grid, i, j)); 
            }
        }
        return res;
    }

    public int dfs(int[][] grid, int i, int j) {
        if(i < 0 || i >= grid.length || j < 0 || j >= grid[0].length || grid[i][j] == 0) return 0;
        int res = 1;
        grid[i][j] = 0;

        for(int[] dir: dirs) {
            res += dfs(grid, i + dir[0], j + dir[1]);
        }
        return res;
    }
}
```

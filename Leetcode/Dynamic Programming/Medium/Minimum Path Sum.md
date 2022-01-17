### Question:
https://leetcode.com/problems/minimum-path-sum/

### Algo:
Recursion, Math

### Sol:
```
class Solution {
    int dp[][];
    public int minPathSum(int[][] grid) {
        dp = new int[grid.length][grid[0].length];
        return minPathSum(grid, 0, 0);
    }
    
    public int minPathSum(int[][] grid, int i, int j) {
        if(i >= grid.length || j >= grid[0].length)
            return Integer.MAX_VALUE;
        
        if(dp[i][j] != 0)
            return dp[i][j];
        
        if(i == grid.length - 1 && j == grid[0].length - 1)
            return grid[i][j];
        
        
        dp[i][j] = Math.min(minPathSum(grid, i + 1, j), minPathSum(grid, i, j + 1)) + grid[i][j];
        return dp[i][j];
    } 
}
```

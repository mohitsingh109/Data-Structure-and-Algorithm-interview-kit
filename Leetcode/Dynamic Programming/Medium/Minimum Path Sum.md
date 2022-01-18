### Question:
https://leetcode.com/problems/minimum-path-sum/

### Algo:
Recursion, Math

### Sol1(Bottom up):
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

### Sol2(Top Down)
```
class Solution {
    public int minPathSum(int[][] grid) {
        
        int row = grid.length;
        int col = grid[0].length;
        int dp[][] = new int[row][col];
        
        dp[0][0] = grid[0][0];
        
        for(int i = 1; i < col; i++)
            dp[0][i] = dp[0][i - 1] + grid[0][i];
        
        for(int i = 1; i < row; i++)
            dp[i][0] = dp[i - 1][0] + grid[i][0];
        
        for(int i = 1; i < row; i++) {
            for(int j = 1; j < col; j++) {
                dp[i][j] = grid[i][j] + Math.min(dp[i - 1][j], dp[i][j - 1]);
            }
        }
        
        return dp[row - 1][col - 1];
    }
}
```

### Reference:
- https://leetcode.com/problems/minimum-path-sum/

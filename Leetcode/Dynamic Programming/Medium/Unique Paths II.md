### Question:
https://leetcode.com/problems/unique-paths-ii/

### Algo:
Matrix

### Sol:
```
class Solution {
    public int uniquePathsWithObstacles(int[][] obstacleGrid) {
        int row = obstacleGrid.length;
        int col = obstacleGrid[0].length;
        
        int [][]dp = new int[row][col];
        
        for(int i = 0; i < col && obstacleGrid[0][i] == 0; i++)
            dp[0][i] = 1;
        
        for(int i = 0; i < row && obstacleGrid[i][0] == 0; i++)
            dp[i][0] = 1;
        
        for(int i = 1; i < row; i++)
            for(int j = 1; j < col; j++) {
               dp[i][j] = obstacleGrid[i][j] == 1? 0: dp[i - 1][j] + dp[i][j - 1]; 
            }
        
        return dp[row - 1][col - 1];
    }
}
```

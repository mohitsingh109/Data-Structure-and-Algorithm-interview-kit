### Question:
https://leetcode.com/problems/unique-paths/

### Algo:
Matrix

### Sol:
```
class Solution {
    public int uniquePaths(int m, int n) {
        int fIndex = Math.min(m , 2);
        int [][]dp = new int[fIndex][n];
        
        for(int i = 0; i < n; i++)
            dp[0][i] = 1;
        
        for(int i = 0; i < fIndex; i++)
            dp[i][0] = 1;
        
        for(int i = 1; i < m; i++)
            for(int j = 1; j < n; j++)
                dp[0][j] = dp[1][j] = dp[0][j] + dp[1][j - 1];
        
        return dp[fIndex - 1][n - 1];
    }
}
```

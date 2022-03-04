### Question:
https://leetcode.com/problems/ones-and-zeroes/

### Algo:
3D array, 0/1 Knapsack

### Sol(2D)
```
class Solution {
    public int findMaxForm(String[] S, int M, int N) {
        int[][] dp = new int[M+1][N+1];
        for (String str : S) {
            int zeros = 0, ones = 0;
            for (char c : str.toCharArray())
                if (c == '0') zeros++;
                else ones++;
            for (int i = M; i >= zeros; i--)
                for (int j = N; j >= ones; j--)
                    dp[i][j] = Math.max(dp[i][j], dp[i-zeros][j-ones] + 1);
        }
        return dp[M][N];
    }
}
So remember that dp[i][j] represents the best possible answer for fitting strings into exactly i zeros and j ones. 
Let's then say that we see a new string with 3 zeros and 4 ones. 
We should then go through every possible dp entry that the new string could possible fit into exactly and check for a better result. 
For dp[8][8], for example, we'd want to check what the result of dp[5][4] is, since that answer plus our current string will exactly fit into 8 by 8. 
So we add 1 to that result (because we're adding the current string) and then check to see if it's better than the current dp[8][8]. 
We then do this for all possible dp entries.
```

### Sol(3D)
```
class Solution {
    int [][][] dp;
    public int findMaxForm(String[] strs, int m, int n) {
        int len = strs.length;
        int [][] arr = new int[len][2];
        dp = new int[len][m + 1][n + 1];
        
        for(int i = 0; i < len; i++) {
            for(char ch: strs[i].toCharArray()) {
                if(ch == '0')
                    arr[i][0]++;
                else 
                    arr[i][1]++;
            }
        }
        
        for(int i = 0; i < len; i++)
            for(int j = 0; j <= m; j++)
            Arrays.fill(dp[i][j], -1);
        
        return subSet(arr, m, n, 0);
    }
    
    
    public int subSet(int [][] arr, int m, int n, int index) {
        if(m + n == 0 || arr.length <= index)
            return 0;
        
        int currentIndex0 = arr[index][0];
        int currentIndex1 = arr[index][1];
        
        
        if(dp[index][m][n] != -1)
            return dp[index][m][n];
    
        
        if(currentIndex0 <= m && currentIndex1 <= n) 
             dp[index][m][n] = Math.max(subSet(arr, m - currentIndex0, n - currentIndex1, index + 1) + 1, subSet(arr, m,  n, index + 1));
             
        dp[index][m][n] = Math.max(subSet(arr, m,  n, index + 1), dp[index][m][n]);
        
        return dp[index][m][n];
    }
}
```

### Reference: 
- https://leetcode.com/problems/ones-and-zeroes/discuss/1138695/JS-Python-Java-C%2B%2B-or-Easy-DP-Knapsack-Solution-w-Explanation

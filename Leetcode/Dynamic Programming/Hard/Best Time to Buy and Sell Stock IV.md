### Question:
https://leetcode.com/problems/best-time-to-buy-and-sell-stock-iv/

### Algo:
DP

### Sol: (N^3)
```
class Solution {
    public int maxProfit(int k, int[] prices) {
        int n = prices.length;
        int dp[][] = new int[k + 1][n];
        
        if(n == 0)
            return 0;
        
        for(int t = 1; t <= k; t++) {
            for(int d = 1; d < n; d++) {
                int max = dp[t][d - 1];
                for(int i = 0; i < d; i++) {
                    max = Math.max(max, prices[d] - prices[i] + dp[t - 1][i]);
                }
                
                dp[t][d] = max;
            }
        }
        
        return dp[k][n - 1];
    }
}
```

### Sol(N^2)
```
class Solution {
    public int maxProfit(int k, int[] prices) {
        int n = prices.length;
        int dp[][] = new int[k + 1][n];
        
        if(n == 0)
            return 0;
        
        for(int t = 1; t <= k; t++) {
            int max = Integer.MIN_VALUE;
            for(int d = 1; d < n; d++) {
                max = Math.max(max, dp[t - 1][d - 1] - prices[d - 1]);
                dp[t][d] = Math.max(max + prices[d], dp[t][d - 1]);
            }
        }
        
        return dp[k][n - 1];
    }
}
```

### Reference:
- https://www.youtube.com/watch?v=3YILP-PdEJA

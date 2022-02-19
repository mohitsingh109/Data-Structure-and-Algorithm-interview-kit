### Question:
https://leetcode.com/problems/best-time-to-buy-and-sell-stock-with-transaction-fee/

### Sol:
DP

### Sol(Top-Down):
```
class Solution {
    
    public int maxProfit(int[] prices, int fee) {
        int[][] dp = new int[prices.length][2];
       
        dp[0][0] = 0;
        dp[0][1] = -prices[0];
        
        for(int i = 1; i < prices.length; i++) {
            
            /*
                if i want to buy today that mean i have sell on previous day
                Math.max(Previous Buy if any, Profit - (buy at today))
            */
            //dp[i][1] = Math.max(PreviousBuy, TotalProfit - currentPrice)
            dp[i][1] = Math.max(dp[i - 1][1], dp[i - 1][0] - prices[i]);

            
            /*
                if i want to sell that mean i have bought it some previous day
                Math.max(Previous Profit, Sell it Today)
            */
            dp[i][0] = Math.max(dp[i - 1][0], dp[i - 1][1] + prices[i] - fee);
            
        }
        
        return dp[prices.length - 1][0];
    }

}   
```

### Sol(Bottom-up)
```
class Solution {
    
    int[][] dp;
    
    public int maxProfit(int[] prices, int fee) {
        dp = new int[prices.length][2];
        for(int [] arr: dp)
            Arrays.fill(arr, -1);
        
        return dfs(prices, 0, true, fee);
    }
    
    
    public int dfs(int[] prices, int day, boolean isBuy, int fee) {
        if(day >= prices.length)
            return 0;
        
        int cIndex = isBuy ? 0: 1;
        
        if(dp[day][cIndex] != -1)
            return dp[day][cIndex];
        
        if(isBuy) {
            int buy = dfs(prices, day + 1, false, fee) - prices[day];
            int skip = dfs(prices, day + 1, true, fee);
            dp[day][cIndex] = Math.max(buy, skip);
        } else {
            int sell = dfs(prices, day + 1, true, fee) + prices[day] - fee;
            int skip = dfs(prices, day + 1, false, fee);
            dp[day][cIndex] = Math.max(sell, skip);
        }
        
        return dp[day][cIndex];
    }
} 
```

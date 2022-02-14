### Question:
https://leetcode.com/problems/best-time-to-buy-and-sell-stock-iii/

### Algo:
DP

### Sol:
```
class Solution {
    public int maxProfit(int[] prices) {
        
        int n = prices.length;
        
        int[] dpl = new int[n];
        int[] dpr = new int[n];
        
        int minLeft = prices[0];
        int maxRight = prices[n - 1];
        
        for(int i = 1; i < n; i++) {
            minLeft = Math.min(prices[i], minLeft);
            dpl[i] = Math.max(dpl[i - 1], prices[i] - minLeft);
        }
        
        for(int i = n - 2; i >= 0; i--) {
            maxRight = Math.max(prices[i], maxRight);
            dpr[i] = Math.max(dpr[i + 1], maxRight - prices[i]);
        }
        
        int profit = 0;
        
        for(int i = 0; i < n; i++) {
            profit = Math.max(profit, dpl[i] + dpr[i]);
        }
        
        return profit;
    }
}
```

### Reference:
- https://www.youtube.com/watch?v=wuzTpONbd-0

### Question:
https://leetcode.com/problems/best-time-to-buy-and-sell-stock-with-cooldown/

### Algo:
DP

### Sol:
```
class Solution {
    
    Map<String, Integer> dp = new HashMap<>();
    
    public int maxProfit(int[] prices) {
        return maxProfit(prices, true, 0);
    }
    
    public int maxProfit(int[] prices, boolean buy, int index) {
        if(index >= prices.length)
            return 0;
        
        String key = "" + index + buy;
        
        if(dp.containsKey(key))
            return dp.get(key);
        
        if(buy) {
            int buyNow = maxProfit(prices, !buy, index + 1) - prices[index];
            int coolDown = maxProfit(prices, buy, index + 1);
            dp.put(key, Math.max(buyNow, coolDown));
        } else {
            int sellNow = maxProfit(prices, !buy, index + 2) + prices[index];
            int coolDown = maxProfit(prices, buy, index + 1);
            dp.put(key, Math.max(sellNow, coolDown));
        }
        
        return dp.get(key);
    }
}
```

### Reference:
- https://www.youtube.com/watch?v=I7j0F7AHpb8

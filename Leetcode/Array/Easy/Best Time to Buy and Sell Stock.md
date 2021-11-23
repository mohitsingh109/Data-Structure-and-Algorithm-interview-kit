### Question:
https://leetcode.com/problems/best-time-to-buy-and-sell-stock/

### Algo:
Array processing

### Sol:
```
class Solution {
    public int maxProfit(int[] prices) {
        int days = prices.length;
        int profit = 0;
        int minPrice = Integer.MAX_VALUE;
        
         for(int i=0; i < days; i++) {
            if(prices[i] < minPrice)
                minPrice = prices[i];
             else if((prices[i] - minPrice) > profit){
                 profit = prices[i] - minPrice;
             }
         }
        
        return profit;
    }
}
```

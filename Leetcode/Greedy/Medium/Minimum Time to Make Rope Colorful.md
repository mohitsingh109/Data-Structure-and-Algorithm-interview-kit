### Question:
https://leetcode.com/problems/minimum-time-to-make-rope-colorful/

### Algo:
Array

### Sol:
```
class Solution {
    public int minCost(String colors, int[] neededTime) {
        
        int prevIndex = 0;
        int cost = 0;
        
        for(int i = 1; i < colors.length(); i++) {
            if(colors.charAt(i) == colors.charAt(prevIndex)) {
                cost += Math.min(neededTime[i], neededTime[prevIndex]);
                if(neededTime[i] > neededTime[prevIndex])
                    prevIndex = i;
            } else {
                prevIndex = i;
            }
        }
        
        return cost;
    }
}
```

### Sol:
```
class Solution {
    public int minCost(String colors, int[] neededTime) {
        
        int cost = 0;
        
        for(int i = 1; i < colors.length(); i++) {
            if(colors.charAt(i) == colors.charAt(i - 1)) {
                cost += Math.min(neededTime[i], neededTime[i - 1]);
                neededTime[i]  = Math.max(neededTime[i], neededTime[i- 1]);
            }
        }
        
        return cost;
    }
}
```

### Question:
https://leetcode.com/problems/gas-station/

### Algo:
Greedy, Math

### Sol:
```
class Solution {
    
    public int canCompleteCircuit(int[] gas, int[] cost) {
        
        int startIndex = 0;
        int totalSurplus = 0;
        int surplus = 0;
            
        for(int i = 0; i < gas.length; i++) {
            totalSurplus += gas[i] - cost[i];
            surplus += gas[i] - cost[i];
            if(surplus < 0) {
                startIndex = i + 1;
                surplus = 0;
            }
        }
        
        return totalSurplus < 0 ? -1: startIndex;
    }

}
```

### Reference:
- https://www.youtube.com/watch?v=xmJZSYSvgfE

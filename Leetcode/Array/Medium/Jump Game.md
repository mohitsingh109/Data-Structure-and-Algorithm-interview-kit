### Question:
https://leetcode.com/problems/jump-game/

### Algo:
DP, Greedy

### Sol(DP):
```
class Solution {
    
    public boolean canJump(int[] nums) {
        int len = nums.length;
        boolean dp[] = new boolean[len];
        dp[0] = true;
        
        for(int i = 0; i < len && dp[len - 1] == false; i++) {
            if(dp[i] == true) {
                int index = Math.min(i + nums[i], len - 1);
                
                if(dp[index] == true)
                    continue;
                
                for(int j = i + 1; j <= Math.min(i + nums[i], len - 1); j++)
                    dp[j] = true;
            } else 
                break;
            
        }
        
        return dp[len - 1];
    }
}
```

### Sol(Greedy)
```
class Solution {
    
    public boolean canJump(int[] nums) {
        int len = nums.length;
        int index = 0;
        int maxRunning = 0;
        
        while(index < len) {
            maxRunning = Math.max(maxRunning - 1, nums[index]);
            if(maxRunning == 0)
                break;
            index++;
        }
        
        return index >= len - 1;
    }
}
```

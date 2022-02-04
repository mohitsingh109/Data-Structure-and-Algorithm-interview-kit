### Question:
https://leetcode.com/problems/jump-game-ii/

### Algo:
DP, Greedy

### Sol (DP):
```
class Solution {
    
    public int jump(int[] nums) {
        int len = nums.length;
        int dp[] = new int[len];
        Arrays.fill(dp, len);
        dp[0] = 0;
        
        for(int i = 0; i < len && dp[len - 1] == len ; i++) {
            int itr = Math.min(len - 1, i + nums[i]);
            for(int j = i + 1; j <= itr; j++) {
                dp[j] = Math.min(dp[j] , dp[i] + 1);
            }
        }
        
        return dp[len - 1];
    }
}   
```

### Sol (Greedy):
```
class Solution {
    
    public int jump(int[] nums) {
        int len = nums.length;
        int r, l, farthest, jump;
        r = l = farthest = jump = 0;
        
        while(r < len - 1) {
            for(int i = l; i <= r; i++) {
                farthest = Math.max(farthest, i + nums[i]);
            }
            
            l = r + 1;
            r = farthest;
            jump++;
        }
        
        return jump;
    }
}   
```

### Reference
- https://www.youtube.com/watch?v=dJ7sWiOoK7g

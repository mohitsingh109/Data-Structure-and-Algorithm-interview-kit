### Question:
https://leetcode.com/problems/house-robber-ii/

### Algo:
DP

### Sol
```
class Solution {
    
    public int rob(int[] nums) {
        if(nums.length == 1)
            return nums[0];
        
        int dp1[] = new int[nums.length];
        int dp2[] = new int[nums.length];
        
        Arrays.fill(dp1, -1);
        Arrays.fill(dp2, -1);
        
        return Math.max(rob(nums, 0, nums.length - 1, dp1), rob(nums, 1, nums.length, dp2));
    }
    
    public int rob(int nums[], int index, int len, int dp[]) {
        if(index >= len) {
            return 0;
        }
        
        if(dp[index] != -1)
            return dp[index];
        
        dp[index] = Math.max(rob(nums, index + 2, len, dp) + nums[index], rob(nums, index + 1, len, dp));
        
        return dp[index];
    }
}
```

### Sol:
```

```

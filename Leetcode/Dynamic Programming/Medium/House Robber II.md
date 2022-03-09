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
class Solution {
    
    public int rob(int[] nums) {
        if(nums.length == 1)
            return nums[0];
        
        return Math.max(rob(nums, 0, nums.length - 1), rob(nums, 1, nums.length));
    }
    
    public int rob(int nums[], int index, int len) {
        int rob1, rob2;
        rob1 = rob2 = 0;
        
        //dp[i] = Max(arr[i] + dp[i-2], dp[i-1])
        //[rob1, rob2, nums[index], nums[index + 1], ....]
        for(int i = index; i < len; i++) {
            int temp = Math.max(nums[i] + rob1, rob2);
            rob1 = rob2;
            rob2 = temp;
        }
        
        // as rob2 reaches the end of array and has max value so we can return it.
        return rob2;
    }
}
```

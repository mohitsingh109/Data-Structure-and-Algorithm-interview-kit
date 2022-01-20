### Question:
https://leetcode.com/problems/house-robber/

### Algo:
backtracing

### Sol:
```
class Solution {
    int dp[];
    public int rob(int[] nums) {
        dp = new int[nums.length];
        Arrays.fill(dp, -1);
        return backTrack(nums, 0);
    }
    
    public int backTrack(int nums[], int index) {
        if(index >= nums.length)
            return 0;
        
        if(dp[index] != -1)
            return dp[index];
        
        dp[index] = Math.max(backTrack(nums, index + 2) + nums[index], backTrack(nums, index + 1));
        return dp[index];
    }
}

```

### Sol:
```
class Solution {
    
    public int rob(int[] nums) {
        int rob1, rob2;
        rob1 = rob2 = 0;
        
        //dp[i] = Max(arr[i] + d[i-2], dp[i-1])
        
        for(int val: nums) {
            int temp = Math.max(val + rob1, rob2);
            rob1 = rob2;
            rob2 = temp;
        }  
        return rob2;
    }
}

```

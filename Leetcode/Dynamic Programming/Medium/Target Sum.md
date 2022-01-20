### Question:
https://leetcode.com/problems/target-sum/

### Algo:
Backtrack, 0/1 Knapsack

### Sol:
```
class Solution {
    int[][] dp;
    int total;
    
    public int findTargetSumWays(int[] nums, int target) {
        total = Arrays.stream(nums).sum();
        
        dp = new int[nums.length][2 * total + 1]; // value can range from [-sum(nums), +sum(nums)]
        
        for (int[] row : dp)
            Arrays.fill(row, Integer.MIN_VALUE);
        
        return  backtrack(nums, target, 0, 0);
    }
    
    public int backtrack(int [] nums, int target, int index, int sum) {
        if(index == nums.length)
            return (target == sum)? 1: 0;
        
        
        if(dp[index][sum + total] == Integer.MIN_VALUE)
            dp[index][sum + total] = backtrack(nums, target, index + 1, sum + nums[index]) +
                   backtrack(nums, target, index + 1, sum - nums[index]);
        
        return dp[index][sum + total];
    }
}
```

### Sol:
```
class Solution {
    
    public int findTargetSumWays(int[] nums, int target) {
        int numberOfZero = 0;
        int total = 0;
        
        for(int val: nums) {
            total += val;
            if(val == 0) numberOfZero++;
        }
        
        int sum = total + target;
        
        //number should be even
        // abs(target) <= sum(arr) 
        if(Math.abs(target) > total || sum % 2 != 0)
            return 0;
        
        sum = sum/2;
        int[][] dp = new int[nums.length + 1][sum + 1];
        
        // how may ways we can create with subset with sum as 0
        for(int i = 0; i <= nums.length; i++)
            dp[i][0] = 1;
        
        // how may ways we can create subset [1 to sum] with empty array {}
        for(int i = 1; i <= sum; i++)
            dp[0][i] = 0;
        
        for(int i = 1; i <= nums.length; i++)
            for(int j = 1; j <=sum; j++) {
                if(nums[i - 1] > j || nums[i - 1] == 0)
                    dp[i][j] = dp[i - 1][j];
                else 
                    dp[i][j] = dp[i - 1][j] + dp[i - 1][j - nums[i - 1]];
            }
        
        return (int)Math.pow(2, numberOfZero) * dp[nums.length][sum];
        
    }

}
```

### Reference:
- https://www.youtube.com/watch?v=hqGa65Rp5LQ
- https://www.youtube.com/watch?v=QihB4bI6BJw
- https://www.youtube.com/watch?v=MqYLmIzl8sQ

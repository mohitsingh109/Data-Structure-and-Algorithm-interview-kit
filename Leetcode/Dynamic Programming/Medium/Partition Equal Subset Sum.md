### Question:
https://leetcode.com/problems/partition-equal-subset-sum/

### Algo:
Subset Sum

### Sol:
```
class Solution {
    public boolean canPartition(int[] nums) {
        int sum = 0;
        for(int val: nums)
            sum += val;
        
        return sum % 2 == 0 && isSubsetWithGivenSum(nums, sum/2);
    }
    
    
    public boolean isSubsetWithGivenSum(int[] arr, int sum) {
        int len = arr.length;
        boolean [][] dp = new boolean[len + 1][sum + 1];
        
        for(int i = 0; i <= len; i++)
            dp[i][0] = true;
        
         for(int i = 1; i <= sum; i++)
            dp[0][i] = false;
        
        for(int j = 1; j <= len; j++) {
            int index = j - 1;
            for(int i = 1; i <= sum; i++){
                if(i < arr[index])
                    dp[j][i] = dp[j - 1][i];
                else 
                    dp[j][i] = dp[j - 1][i] || dp[j - 1][i - arr[index]];
            }
        }
        
        return dp[len][sum];
    }
}
```

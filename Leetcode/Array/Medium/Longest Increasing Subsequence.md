### Question:
https://leetcode.com/problems/longest-increasing-subsequence/

### Algo:
DP

### Sol:
```
class Solution {
    public int lengthOfLIS(int[] nums) {
        int maxLen = 0;
        int[] count = new int[nums.length];
        
        int start = -1;
        for(int i = 0; i < nums.length; i++) {
            int currMax = 1;
            for(int j = start; j >= 0; j--) {
                if(nums[i] > nums[j]) {
                    currMax = Math.max(count[j] + 1, currMax);
                }
            }
            start = i;
            count[i] = currMax;
            maxLen = Math.max(maxLen, currMax);
        }
        
        return maxLen;   
    }     
}
```

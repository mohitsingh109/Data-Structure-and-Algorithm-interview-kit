### Question
https://leetcode.com/problems/subarray-sum-equals-k/

### Algo:
Prefix Sum

### Sol:
```
class Solution {
    public int subarraySum(int[] nums, int k) {
        
        int count = 0;
        Map<Integer, Integer> prefixSum = new HashMap<>();
        prefixSum.put(0, 1);
        int runningSum = 0;
        
        for(int i = 0; i < nums.length; i++) {
            runningSum += nums[i];
            count += prefixSum.getOrDefault(runningSum - k, 0);
            prefixSum.put(runningSum, prefixSum.getOrDefault(runningSum, 0) + 1);
        }
        
        return count;
    }
}
```

### Reference:
- https://www.youtube.com/watch?v=fFVZt-6sgyo

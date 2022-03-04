### Question:
https://leetcode.com/problems/minimum-size-subarray-sum/

### Algo:
Two Pointer

### Sol:
```
class Solution {
    public int minSubArrayLen(int target, int[] nums) {
        int result = nums.length + 1;
        int startWindow = 0;
        int sum = 0;
        
        for(int endWindow = 0; endWindow < nums.length; endWindow++) {
            sum += nums[endWindow];
            
            while(sum >= target && startWindow <= endWindow) {
                result = Math.min(result, endWindow - startWindow + 1);
                sum -= nums[startWindow++];
            }
        }
        
        return result == nums.length + 1? 0: result;
    }
}
```

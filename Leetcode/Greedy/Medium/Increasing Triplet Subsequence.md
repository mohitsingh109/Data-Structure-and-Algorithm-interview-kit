### Question:
https://leetcode.com/problems/increasing-triplet-subsequence/

### Algo:
Math

### Sol:
```
class Solution {
    public boolean increasingTriplet(int[] nums) {
        int first, second;
        first = second = Integer.MAX_VALUE;
        
        for(int i = 0; i < nums.length; i++) {
            if(first >= nums[i]) {
                first = nums[i];
            } else if(second >= nums[i]) {
                second = nums[i];
            } else {
                return true;
            }
        }
        
        return false;
    }
}
```

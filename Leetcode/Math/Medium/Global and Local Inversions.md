### Question:
https://leetcode.com/problems/global-and-local-inversions/

### Algo:
Math

### Sol:
```
class Solution {
    public boolean isIdealPermutation(int[] nums) {
        
       int max = -1;
        
        for(int i = 0; i < nums.length - 2; i++) {
            max = Math.max(max, nums[i]);
            if(max > nums[i + 2])
                return false;
        }
        
        return true;
    }
}
```

### Sol:
```
class Solution {
    public boolean isIdealPermutation(int[] nums) {
        
        for(int i = 0; i < nums.length; i++) {
            if(Math.abs(nums[i] - i) > 1)
                return false;
        }

        return true;
    }
}
```

### Reference:
- https://www.youtube.com/watch?v=1QlP6cVLrII

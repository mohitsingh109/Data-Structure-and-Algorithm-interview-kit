### Question:
https://leetcode.com/problems/move-zeroes/

### Algo:
Two Pointers

### Sol:
```
class Solution {
    public void moveZeroes(int[] nums) {
        int len = nums.length;
        if(len <= 1)
            return;
        
        int left = 0, right = 0;
        while(right < len) {
            if(nums[right] == 0)
                right++;
            else {
                int temp = nums[right];
                nums[right] = nums[left];
                nums[left] = temp;
                left++;
                right++;
            }
        }
    }
}
```

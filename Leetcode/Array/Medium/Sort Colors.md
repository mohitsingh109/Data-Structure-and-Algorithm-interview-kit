### Question:
https://leetcode.com/problems/sort-colors/

### Algo:
Two Pointer, Sort

### Sol:
```
class Solution {
    public void sortColors(int[] nums) {
        
        int low = 0;
        int mid = 0;
        int high = nums.length - 1;
        
        while(mid <= high) {
            if(nums[mid] == 2) {
                nums[mid] = nums[high];
                nums[high] = 2;
                high--;
            } else if(nums[mid] == 0) {
                int temp = nums[mid];
                nums[mid] = nums[low];
                nums[low] = temp;
                low++;
                mid ++;
            } else {
                mid ++;
            }
        }
    }
}

```

### Question:
https://leetcode.com/problems/next-permutation/

### Algo:
Math, Permutation Graph

### Sol:
```
class Solution {
    public void nextPermutation(int[] nums) {
        
        int i = nums.length - 2;
        
        while(i >=0 && nums[i] >= nums[i + 1]) i--;
        
        if(i >=0) {
            int j = nums.length - 1;
            while(j >=0 && nums[i] >= nums[j]) j--;
            swap(nums, i, j);
        }
        
        reverse(nums, i + 1, nums.length - 1);
    }
    
    
    public void reverse(int[] arr, int start, int end) {
        while(start < end) {
            swap(arr, start, end);
            start++;
            end--;
        }
    }
    
    public void swap(int[] arr, int i, int j) {
        int temp = arr[i];
        arr[i] = arr[j];
        arr[j] = temp;
    }
}
```

### Reference:
- https://www.youtube.com/watch?v=LuLCLgMElus&t=459s

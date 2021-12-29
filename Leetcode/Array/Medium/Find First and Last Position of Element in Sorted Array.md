### Question:
https://leetcode.com/problems/find-first-and-last-position-of-element-in-sorted-array/

### Algo:
Binary Search

### Sol:
```
class Solution {
    public int[] searchRange(int[] nums, int target) {
       return new int[]{firstIndex(nums, target), lastIndex(nums, target)};
    }
    
    
    public int firstIndex(int[] arr, int target) {
        int index = -1;
        
        int left = 0;
        int right = arr.length - 1;
        
        while(left <= right) {
            int mid = (left + right)/2;
            if(arr[mid] == target) {
                right = mid - 1;
                index = mid;
            } else if(arr[mid] < target) {
                left = mid + 1;
            } else right = mid - 1;
        }
        
        return index;
    }
    
    public int lastIndex(int[] arr, int target) {
        int index = -1;
        
        int left = 0;
        int right = arr.length - 1;
        
        while(left <= right) {
            int mid = (left + right)/2;
            if(arr[mid] == target) {
                left = mid + 1;
                index = mid;
            } else if(arr[mid] < target) {
                left = mid + 1;
            } else right = mid - 1;   
        }
        
        return index;
    }
}
```

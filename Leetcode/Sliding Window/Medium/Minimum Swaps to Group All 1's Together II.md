### Question:
https://leetcode.com/problems/minimum-swaps-to-group-all-1s-together-ii/

### Algo:
Array

### Sol:
```
class Solution {
    public int minSwaps(int[] nums) {
        int arr[] = new int[nums.length * 2];
        
        int numberOf1 = 0;
        
        // merge array to handel circular path
        for(int i = 0; i < nums.length; i++) {
            numberOf1 += nums[i];
            arr[i] = arr[i + nums.length] = nums[i];
        }
    
        return minSwapInternal(arr, numberOf1);
    }
    
    public int minSwapInternal(int[] nums, int numberOf1) {
        
        if(numberOf1 == 0)
            return 0;
        
        int ans = nums.length;
        int windowStart = 0;
        int count = 0;
        
        for(int i = 0; i < nums.length; i++) {
            count += nums[i] == 0? 1: 0;
            if(i >= numberOf1 -1) {
                ans = Math.min(count, ans);
                count -= nums[windowStart] == 0? 1: 0;
                windowStart++;
            }
        }
        
        return ans;
    }
}
```

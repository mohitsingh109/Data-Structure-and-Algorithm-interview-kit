### Question:
https://leetcode.com/problems/sum-of-all-subset-xor-totals/

### Algo:
Backtracking, Recursion, Subset

### Sol:
```
class Solution {
    public int subsetXORSum(int[] nums) {
        return calSubsetXORSum(nums, 0, 0);
    }
    
     public static int calSubsetXORSum(int[] nums, int idx, int xor) {
        if(idx >= nums.length)
            return xor;
         
         return calSubsetXORSum(nums, idx + 1, nums[idx] ^ xor) + calSubsetXORSum(nums, idx + 1, xor);
    }
}
```

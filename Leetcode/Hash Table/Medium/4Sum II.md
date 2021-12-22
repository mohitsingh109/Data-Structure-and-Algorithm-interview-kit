### Question:
https://leetcode.com/problems/4sum-ii/

### Algo:
Math

### Sol:
```
class Solution {
    public int fourSumCount(int[] nums1, int[] nums2, int[] nums3, int[] nums4) {
        Map<Integer, Integer> map = new HashMap<>();
        int count = 0;
        
        for(int val1 : nums1) {
            for(int val2: nums2) {
                int sum = val1 + val2;
                map.put(sum, map.getOrDefault(sum, 0) + 1);
            }
        }
        
        for(int val1 : nums3) {
            for(int val2: nums4) {
                int sum = val1 + val2;
                count += map.getOrDefault(-sum, 0);
            }
        }
        
        return count;
    }
}

// Formula
// A[i] + B[j] = -(C[k] + D[l])
```

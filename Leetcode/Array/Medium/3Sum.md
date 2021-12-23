### Question:
https://leetcode.com/problems/3sum/

### Algo:
Two Pointer, Sort

### Sol:
```
class Solution {
    public List<List<Integer>> threeSum(int[] nums) {
        
        Arrays.sort(nums); // nlogn
        List<List<Integer>> res = new ArrayList<>();
        
        for(int i = 0; i < nums.length - 2; i++) { // n * n
            if (i > 0 && nums[i] == nums[i - 1])
                continue;
            
            int start = i + 1;
            int end = nums.length - 1;
            
            while(start < end) {
                int sum = nums[start] + nums[end];
                if(sum == -1 * nums[i]) {
                    res.add(Arrays.asList(nums[i], nums[start], nums[end]));
                    while(start < end && nums[start] == nums[start + 1]) start++; 
                    while(start < end && nums[end] == nums[end - 1]) end--; 
                    start++;
                    end--;
                } else if(sum > -1 * nums[i])
                    end--;
                else 
                    start++;
            }
        }
        
        return res;
    }
}
```

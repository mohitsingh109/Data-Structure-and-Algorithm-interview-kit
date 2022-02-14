### Question:
https://leetcode.com/problems/minimum-operations-to-make-the-array-alternating/

### Algo:
Frequency

### Sol:
```
class Solution {
    public int minimumOperations(int[] nums) {
        
        if(nums.length == 1)
            return 0;
        
        Map<Integer, Integer> evenCount = new HashMap<>();
        Map<Integer, Integer> oddCount = new HashMap<>();
        
        int maxEven = 0;
        int maxOdd = 0;
        int evenElement = nums[0];
        int oddElement = nums[1];
        
        for(int i = 0; i < nums.length; i+=2) {
            evenCount.put(nums[i], evenCount.getOrDefault(nums[i], 0) + 1);
            if(maxEven < evenCount.get(nums[i])){
                maxEven = evenCount.get(nums[i]);
                evenElement = nums[i];
            }
        }
        
        for(int i = 1; i < nums.length; i+=2) {
            oddCount.put(nums[i], oddCount.getOrDefault(nums[i], 0) + 1);
            if(maxOdd < oddCount.get(nums[i])){
                maxOdd = oddCount.get(nums[i]);
                oddElement = nums[i];
            }
        }
        

        if(evenElement != oddElement) {
            return (nums.length - maxOdd - maxEven);
        }
        
        evenCount.remove(evenElement);
        oddCount.remove(oddElement);
        
        int nextEvenMax = 0;
        int nextOddMax = 0;
        
        for(Integer key: evenCount.keySet()) {
            nextEvenMax = Math.max(nextEvenMax, evenCount.get(key));
        }
        
        for(Integer key: oddCount.keySet()) {
            nextOddMax = Math.max(nextOddMax, oddCount.get(key));
        }
        
        return Math.min(nums.length - maxEven - nextOddMax, nums.length - nextEvenMax - maxOdd);
    }
}
```

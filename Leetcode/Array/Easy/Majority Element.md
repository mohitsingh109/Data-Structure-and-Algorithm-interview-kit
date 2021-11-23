### Question: 
https://leetcode.com/problems/majority-element/

### Algo:
Moore's Voting Algorithm

### Sol:
```
class Solution {
    public int majorityElement(int[] nums) {
        
        int element = nums[0];
        int elementCount = 1;
        for(int i = 1; i < nums.length; i++){
            if(element == nums[i])
                elementCount++;
            else if(--elementCount == 0){
                element = nums[i];
                elementCount = 1;
            }
        }
        
        // This is to check if element is really present or not
        // as per question it's always present so we can skip this code
         // elementCount = 0;
         // for(int i = 0; i < nums.length; i++){
         //     if(element == nums[i])
         //        elementCount++
         // }
        
        return element;
    }
}
```

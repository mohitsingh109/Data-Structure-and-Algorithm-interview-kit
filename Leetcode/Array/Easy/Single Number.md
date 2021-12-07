### Question
https://leetcode.com/problems/single-number/

### Algo:
XOR

### Sol:
```
class Solution {
    public int singleNumber(int[] nums) {
        int num = 0;
        for(int i = 0; i < nums.length; i++)
            num = num ^ nums[i];
        
        return num;
    }
}
```

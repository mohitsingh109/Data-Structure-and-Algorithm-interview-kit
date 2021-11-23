### Question:
https://leetcode.com/problems/missing-number/

### Algo:
Math, XOR

### Sol-1:
```
class Solution {
    public int missingNumber(int[] nums) {
        int len = nums.length;
        int sum = (len * (len +1))/2;
        
        for(int val: nums){
            sum-=val;
        }
        
        return sum;
    }
}

```
### Sol-2:
```
class Solution {
   public int missingNumber(int[] nums) {
    int sum = 0;
    for (int i = 0; i <= nums.length; ++i) sum ^= i;
    for (int i = 0; i < nums.length; ++i) sum ^= nums[i];
    return sum;
    }
}

```

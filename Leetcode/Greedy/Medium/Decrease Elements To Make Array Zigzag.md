### Question:
https://leetcode.com/problems/decrease-elements-to-make-array-zigzag/

### Algo:
Array

### Sol:
```
class Solution {
    public int movesToMakeZigzag(int[] nums) {
        
        int evenMove = 0;
        int oddMove = 0;
        
        int first = -1;
        int second = -1;
        
        //even index case
        for(int i = 0; i < nums.length - 1; i++) {
           
            if(i == 0) {
                first = nums[i];
                second = nums[i + 1];
            } else {
                second = nums[i + 1];
            }
            
            if(i % 2 == 0) {
                if(second >= first) {
                    evenMove += second - first + 1;
                    second = first - 1;
                }
            } else {
                if(first >= second) {
                    evenMove += first - second + 1;
                }
            }
            
            first = second;
        }
        
        //odd index case
        for(int i = 0; i < nums.length - 1; i++) {
           
            if(i == 0) {
                first = nums[i];
                second = nums[i + 1];
            } else {
                second = nums[i + 1];
            }
            
            if(i % 2 == 0) {
                if(first >= second) {
                    oddMove += first - second + 1;
                }
            } else {
                if(second >= first) {
                    oddMove += second - first + 1;
                    second = first - 1;
                }
            }
            
            first = second;
        }
        
        
       return Math.min(evenMove, oddMove);
    }
}

```

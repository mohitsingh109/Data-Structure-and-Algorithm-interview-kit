### Question:
https://leetcode.com/problems/container-with-most-water/

### Algo:
Two Pointer

### Sol:
```
class Solution {
    public int maxArea(int[] height) {
        int start = 0;
        int end = height.length - 1;
        int max = 0;
        
        while(start < end) {
            int verticalLen = Math.min(height[start], height[end]);
            max = Math.max(max, verticalLen * (end - start));
            
            if(height[start] == verticalLen)
                start++;
            else end--;
        }
        
        return max;
    }
}
```

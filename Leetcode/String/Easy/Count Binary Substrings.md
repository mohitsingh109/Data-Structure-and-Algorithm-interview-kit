### Question:
https://leetcode.com/problems/count-binary-substrings/

### Algo:
Two Pointer

### Sol:
```
class Solution {
    public int countBinarySubstrings(String s) {
        int curr = 1, prev = 0, count = 0;
        
        for(int i = 1; i < s.length(); i++) {
            if(s.charAt(i) == s.charAt(i-1))
                curr++;
            else {
                count += Math.min(prev, curr);
                prev = curr;
                curr = 1;
            }
        
        }
        
        return count + Math.min(prev, curr);
    }
}
```

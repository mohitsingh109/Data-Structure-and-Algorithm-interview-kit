### Question:
https://leetcode.com/problems/palindromic-substrings/

### Algo:
Expend Left, Right

### Sol:
```
class Solution {
    public int countSubstrings(String s) {
        
        int res = 0;
        
        for(int i = 0; i < s.length(); i++) {
            res += palindromCount(s, i, i);
            res += palindromCount(s, i, i + 1);
        }
        
        return res;
    }
    
    public int palindromCount(String s, int left, int right) {
        int count = 0;
        
        while(left >= 0 && right < s.length() && s.charAt(left) == s.charAt(right)) {
            left--;
            right++;
            count++;
        }
        
        return count;
    }
}
```

### Reference
- https://www.youtube.com/watch?v=4RACzI5-du8

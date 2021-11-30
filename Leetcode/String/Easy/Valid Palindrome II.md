### Question:
https://leetcode.com/problems/valid-palindrome-ii/

### Algo:
Greedy, Two Pointer

### Sol:
```
class Solution {
    public boolean validPalindrome(String s) {
        return helperValidPalindrome(s, 0, s.length() - 1, 0);
    }
    
    public static boolean helperValidPalindrome(String s, int start, int end ,int level) {
        if(level > 1)
            return false;
        
        while(start < end) {
            if(s.charAt(start) != s.charAt(end)) {
                return helperValidPalindrome(s, start, end - 1, level + 1) || 
                    helperValidPalindrome(s, start + 1, end, level + 1);
            }else{
                start++;
                end--;
            }
        }
        
        return true;
    }
}
```

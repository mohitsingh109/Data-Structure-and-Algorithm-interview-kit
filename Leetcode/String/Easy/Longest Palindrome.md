### Question:
https://leetcode.com/problems/longest-palindrome/

### Algo:
Hash Table, Greedy

### Sol:
```
class Solution {
    public int longestPalindrome(String s) {
        int [] arr = new int[128];
        int oddCount = 0;
        
        for(int i = 0; i < s.length(); i++)
            arr[s.charAt(i)]++;
        
        for(int i = 0; i < 128; i++)
            oddCount += arr[i] & 1;
        
        
        return s.length() - oddCount + (oddCount > 0? 1: 0);
    }
}
```

### Question:
https://leetcode.com/problems/longest-nice-substring/

### Algo:
Set, Divide & Conquer

### Sol:
```
class Solution {
    public String longestNiceSubstring(String s) {
        if(s == null || s.length() < 2)
            return "";
        
        Set<Character> set = new HashSet<>();
        
        for(int i =0; i < s.length(); i++) {
            set.add(s.charAt(i));
        }
        
        for(int i =0; i < s.length(); i++) {
            char ch = s.charAt(i);
            if(set.contains(Character.toLowerCase(ch)) && set.contains(Character.toUpperCase(ch)))
               continue;
            String sub1 = longestNiceSubstring(s.substring(0, i));
            String sub2 = longestNiceSubstring(s.substring(i + 1));
            
            return sub1.length() >= sub2.length()? sub1: sub2;
        }
        
        return s;
    }
}
```

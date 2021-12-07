### Question
https://leetcode.com/problems/longest-substring-without-repeating-characters/

### Algo:
Sliding Window, HashSet

### Sol1:
```
class Solution {
    public int lengthOfLongestSubstring(String s) {
        
        int startIndex = 0;
        Map<Character, Integer> seen = new HashMap<>();
        int maxlen = 0;
        for(int endIndex = 0; endIndex < s.length(); endIndex++) {
            char ch = s.charAt(endIndex);
            if(seen.containsKey(ch)) {
                startIndex = Math.max(startIndex, seen.get(ch) + 1);
            }
            seen.put(ch, endIndex);
            maxlen = Math.max(maxlen, endIndex - startIndex + 1);
        }
        
        return maxlen;
    }
}
```

### Sol2:
```
class Solution {
    public int lengthOfLongestSubstring(String s) {
        
        int startIndex = 0;
        Set<Character> seen = new HashSet<>();
        int maxlen = 0;
        for(int endIndex = 0; endIndex < s.length(); endIndex++) {
            char ch = s.charAt(endIndex);
            while(startIndex < endIndex && seen.contains(ch)) {
                seen.remove(s.charAt(startIndex++));
            }
            
            seen.add(ch);
            maxlen = Math.max(maxlen, seen.size());
        }
        
        return maxlen;
    }
}
```
